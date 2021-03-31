# lotus-openrpc-client

Lotus API client in Typescript generated from the the OpenRPC definitions.

_Generated with [open-rpc/generator] from [lotus 1.7.0-dev openrpc definition](https://github.com/filecoin-project/lotus/tree/f4a2c8fa49dfc456090f5a5ea1b4ae62d33b4f85/build/openrpc)_

⚠️ This is currently an exploration to see what is possible; not for consumption. ⚠️

## Provenance

Get the openrc definitions from the lotus repo, ungzip them, and pass them to the [open-rpc/generator].

```shell
# ungzip the lotus full node openrpc definition
curl "https://raw.githubusercontent.com/filecoin-project/lotus/f4a2c8fa49dfc456090f5a5ea1b4ae62d33b4f85/build/openrpc/full.json.gz" | zcat > full.json 

# create the typescript rpc client
npx @open-rpc/generator generate -t client -l typescript -n "lotus-openrpc-client" -d full.json 
```

A copy of the uncompressed and prettfied openrpc definitons for lotus can be found in this gist: https://gist.github.com/olizilla/fc6abf836023b6ee662955695f1cfd21

You can preview the generated OpenRPC docs for the Lotus API by passing the files in that gist to the OpenRPC playground. See here for the docs for the Lotus full node api: https://playground.open-rpc.org/?url=https://gist.githubusercontent.com/olizilla/fc6abf836023b6ee662955695f1cfd21/raw/a4cb5aa3c6fbbc47bcf4b92d2370b8b012a810cb/full.json


## Background

[OpenRPC] is a spec for defining / documenting your [JSON-RPC] compatibale api. With an OpenRPC definitinon for you API, you can automatically generate API clients and documentation with [open-rpc/generator]

The Lotus Filecoin implementation landed OpenRPC definintions for it's API in https://github.com/filecoin-project/lotus/pull/5843

The rationale for OpenRPC (as opposed to the widely deployed OpenAPI) is given here 
> This project [openrpc] is a fork of openapi. It was modified to accommodate JSON-RPC APIs.
>
> While you could get some things to work, using openapi on anything but path & http based api is fitting a round peg to a square hole.
> – https://github.com/open-rpc/spec/issues/112

Lotus uses a custom go json-rpc client https://github.com/filecoin-project/go-jsonrpc

The [open-rpc/generator] currently fails to build a working docs site https://github.com/open-rpc/generator/issues/621

## TODO

- [ ] use the client to get some data in and out of a lotus node.
- [ ] Fix the rough edges. This version has some mad robot types that no human is gonna want to see in there editor.
- [ ] Set up CI to publish updates to the client when the Lotus OpenRPC definitions change.


[OpenRPC]: https://open-rpc.org/ "defines a standard, programming language-agnostic interface description for JSON-RPC 2.0 APIs."
[JSON-RPC]: https://www.jsonrpc.org/specification "a stateless, light-weight remote procedure call (RPC) protocol."
[open-rpc/generator]: https://github.com/open-rpc/generator "Multi-Component & Multi-Language Generators for OpenRPC"
