# Currency_Convertor 💸

> Lightweight currency conversion library.

[![cashify at docs.rs](https://docs.rs/cashify/badge.svg)](https://docs.rs/cashify)

## Usage

The following example uses [Serde JSON](https://github.com/serde-rs/json) as strongly typed data structures. Instead of manually specifying rates, you can obtain them from an API, like [Exchange Rates API](https://exchangeratesapi.io/).

```rust
use std::collections::HashMap;
use serde::{Deserialize, Serialize};
use serde_json::Result;
use cashify::{convert};

#[derive(Serialize, Deserialize)]
struct Rates<'a>{
    base: &'a str,
    rates: HashMap<&'a str, f64>
}

fn main() -> Result<()> {
      let data = r#"{
          "base": "EUR",
          "rates": {
              "GBP": 0.92,
              "EUR": 1
          }
      }"#;
  
      let r: Rates = serde_json::from_str(data)?;

      println!("The result is: {}", convert(10.0, "EUR", "GBP", r.base, r.rates));
      Ok(())
}
```

## Roadmap

The goal is to try and implement as much features from the original Currency_Convertor as possible.

- [x] `convert` Function
- [ ] Constructor
- [ ] Parsing

## License
MIT
