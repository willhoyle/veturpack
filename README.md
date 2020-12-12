# Repro for vetur
issue: https://github.com/vuejs/vetur/issues/2559

## how to repro

```
git clone git@github.com:willhoyle/veturpack.git
cd veturpack
sudo chmod -R 333 data # this will remove read access privileges for data folder
code .
```

Go to the Output tab in the terminal, you'll see something similar to the following error:

```bash
[Error - 1:04:28 PM] Request textDocument/documentSymbol failed.
  Message: Request textDocument/documentSymbol failed with message: EACCES: permission denied, scandir '/home/will/projects/veturpack/data'
  Code: -32603
```

The status bar at the bottom of vs code will display: `Load project: /home/will/projects/veturpack` and never resolve. The vetur extension won't work in this state (formatting `.vue` files doesn't work)

## Expected behaviour
vetur should ignore folders it has no read access to (or outputs a warning message instead of error)