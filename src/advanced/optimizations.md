## Optimization

Because Substrate is written in Rust, writing optimized Rust code reduces runtime overhead (costs) for Substrate deployments. Likewise, it is important to write clean, high-performance Rust code. There are a few tips here.

We call an algorithm "efficient" if its running time is polynomial in the size of the input, and "highly efficient" if its running time is linear in the size of the input. It is important for all on-chain algorithms to be highly efficient, because they must scale well as the size of the Polkadot network grows. In contrast, off-chain algorithms are only required to be efficient. [src](http://research.web3.foundation/en/latest/polkadot/NPoS/1.intro/)

* `troubles.md` post

## Iterate Through a Slice Rather than a Vec!

It's noticeably faster to iterate over a slice rather than a `vec!`.

* `.iter.map(|x| x.0.into()).collect`

### MISC NOTES

* MAPS USE BLAKE2
* STORAGE VALUES USE TWOX

BLAKE2 IS 6X SLOWER THAN TWOX
but if you have keys in your map, that can be manipulated from the outside; an attacker could try to create hash collisions.
Moreover, for the map, you can set the hasher you want to use => look up the correct hash for your type in the metadata.