# Spanreed

Project goal: add an integration layer between automerge and client code, compatible with any async runtime.

## Examples 

### Multipe TCP clients, one server with hardcoded IP, in memory storage.

1. Start the server:
   - `cargo run --example tcp-example -- --tcp-run-ip 127.0.0.1:2345 --http-run-ip 0.0.0.0:3001`
2. Start any number of clients:
   - `cargo run --example tcp-example -- --other-ip 127.0.0.1:2345 --http-run-ip 0.0.0.0:3002`
3. Create a new document at the server:
   - `curl 0.0.0.0:3001/new_doc`
   - The document id is returned as json.
4. Request the document:
   - `curl --json '{document-id}' 0.0.0.0:3002/request_doc` 
5. Presss ctr-c at every terminal tab.
6. A successful run will print out the expected synced documents. 