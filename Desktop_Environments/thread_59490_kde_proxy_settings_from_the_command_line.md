---
title: "kde proxy settings from the command line"
date: 2005-08-24
forum: Desktop Environments
---

### Post by PeP on 2005-08-24
I want to make a script to configure my proxy automatically from whereami (automatic detection of the network environment)

I see three solutions:
1. Find a way to set the kde proxy from the command line (dcop call or something)
2. Find a way to make  $http_proxy  global (export -p /declare -x don 't work for we're in X environnment)
3. Set up a tinyproxy and cp -f specific configurations with or without redirections, then restart it.

I know how to do the last one, but if someone can show me for either 1. or 2. it would be great :-)

Edit: I have the same problem with synaptic, any hint ??

---

