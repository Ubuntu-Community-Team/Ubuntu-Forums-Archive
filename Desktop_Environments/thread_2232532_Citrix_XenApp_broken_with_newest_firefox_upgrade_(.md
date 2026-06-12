---
title: "Citrix XenApp broken with newest firefox upgrade (version 30+)"
date: 2014-07-02
forum: Desktop Environments
---

### Post by Hypnoz on 2014-07-02
I wanted to provide info to the community in case anyone uses Citrix XenApp, and recently upgraded firefox only to find that Citrix XenApp doesn't work anymore. After logging in, you click an application and get a spinning wheel for a few seconds, then nothing. There is no error message.

After some research, I found a page with the fix:

> Note: There is a problem launching the Citrix Receiver on Ubuntu 14.04 LTS which is the direct result of upgrading to FireFox 30.0. The Citrix Receiver Client plugin is set to ask to activate in the upgraded version of the browser which is the setting preventing the receiver from launching.

To fix the security setting for the Citrix Receiver in FireFox 30:
Add-ons -> Plugins -> Citrix Receiver for Ubuntu -> Set to always activate

Thanks to: [http://blog.vinnymac.org/?p=351](http://blog.vinnymac.org/?p=351)

-Colin

---

