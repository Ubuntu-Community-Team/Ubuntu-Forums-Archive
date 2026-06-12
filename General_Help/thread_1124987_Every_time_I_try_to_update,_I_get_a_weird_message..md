---
title: "Every time I try to update, I get a weird message."
date: 2009-04-13
forum: General Help
---

### Post by ninjaaron on 2009-04-13
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

[then inside a white box it says]
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFFFailed to fetch [http://javadesktop.org/lg3d/debian/dists/testing/contrib/binary-amd64/Packages.gz](http://javadesktop.org/lg3d/debian/dists/testing/contrib/binary-amd64/Packages.gz)  404 Not Found


Then I can download some updates, but I expect I am missing something important. What's the deal?

PS. went for a long time without updating my system because I have dial-up at home. Maybe I missed something important?

---

### Post by aaronp on 2009-04-14
Try going to System>Administration>Software Sources.
In the third party software tab you will probably see a URL that is familiar from your error message. 

Disable it then see if the error re-appears when trying to update sources again.

---

### Post by dcstar on 2009-04-14
> **ninjaaron said:**
> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

[then inside a white box it says]
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFFFailed to fetch [http://javadesktop.org/lg3d/debian/dists/testing/contrib/binary-amd64/Packages.gz](http://javadesktop.org/lg3d/debian/dists/testing/contrib/binary-amd64/Packages.gz)  404 Not Found


Then I can download some updates, but I expect I am missing something important. What's the deal?

PS. went for a long time without updating my system because I have dial-up at home. Maybe I missed something important?

There were notices a while ago about updating ppa repository keys.

---

### Post by ninjaaron on 2009-04-14
> **dcstar said:**
> There were notices a while ago about updating ppa repository keys.

What is ppa, and where do I find the new repository keys?

---

