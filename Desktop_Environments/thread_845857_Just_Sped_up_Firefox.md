---
title: "Just Sped up Firefox"
date: 2008-07-01
forum: Desktop Environments
---

### Post by SuperMike on 2008-07-01
I made a discovery that speeds up FF. It has a small caveat.

I noticed that my FF was very slow on https connections no matter where I went. This is because the https key sizes are having to get bigger and bigger every few years to fend off the encryption crackers on the Internet.

Well, in https (aka SSL) connections, there is a version 2 and a version 3. Most new web servers, if SSL is enabled, are running support for both versions so that older browsers can still connect.

Normally when you connect, you're running SSLv3 from FF to the server at the highest key size (thus packet size) that both can support. Talk about slooooow. Okay, fine. Now go into FF's about:config like so:

about:config  <-- type in a new tab in your URL field.

Now hunt for ssl stuff by typing "ssl" in the search field.

Okay, now switch off only the item that says enable SSLv3, but turn on the item that says enable SSLv2. As well, you'll also have to find all the SSLv2 protocols under that enable SSLv2 item and switch all of those on as well.

Shut down your browser, come back in, and then connect to a site like Gmail but on https instead of http. Your performance will like double. It will be zippy fast, but only on https type sites.

Okay, here's the caveat. Some web servers are only running SSLv3, so you'll have to undo this occasionally when needing to connect to them.

Would be nice if there was an SSLv2 to SSLv3 toggle switch you could enable through an AddOn in FF.

---

### Post by Bubba64 on 2008-07-01
You might try this.
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

---

### Post by sonofusion82 on 2008-07-01
> **SuperMike said:**
> Normally when you connect, you're running SSLv3 from FF to the server at the highest key size (thus packet size) that both can support. Talk about slooooow. 

The slowness is more due to the addition computation power need for the more complex cryptographic algorithms with larger key sizes. The increased key size will only slightly increases the packet size by a few hundred bytes since it is only used during the initial handshake compared to the actual payload of a few hundred KB of a typical web page.

To me, compromising security for performance is not exactly a good choice. There are better ways to improve FF performance such as suggested by Bubba64 or just google for firefox performance tuning or optimizing

---

