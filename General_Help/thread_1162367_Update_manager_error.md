---
title: "Update manager error"
date: 2009-05-17
forum: General Help
---

### Post by Swatfoot on 2009-05-17
getting this error from update manager.

( W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

W: Failed to fetch [http://packages.medibuntu.org/dists/jaunty/Release](http://packages.medibuntu.org/dists/jaunty/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead. )

OK removed that source in software sources and that fixed it for now.
probably need the right key.

---

### Post by mb_webguy on 2009-05-17
Try "sudo apt-get install medibuntu-keyring && sudo apt-get install update" in the terminal.

---

