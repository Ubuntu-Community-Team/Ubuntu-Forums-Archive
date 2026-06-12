---
title: "Using automatic proxy scripts with gnome-terminal"
date: 2010-07-29
forum: Desktop Environments
---

### Post by Linfreak on 2010-07-29
Hi all,

My laptop is behind a proxy and I use a proxy url like [http://proxyconf/proxy.pac](http://proxyconf/proxy.pac) in firefox for connecting to the internet.

Using the same in terminal like below,

export http_proxy=http://proxyconf/proxy.pac

I am not able to download stuff with say wget. Example terminal output below.

wget -c [http://fi.archive.ubuntu.com/ubuntu/pool/main/libe/libemail-valid-perl/libemail-valid-perl_0.15-3_all.deb](http://fi.archive.ubuntu.com/ubuntu/pool/main/libe/libemail-valid-perl/libemail-valid-perl_0.15-3_all.deb)
--2010-07-29 12:31:16--  [http://fi.archive.ubuntu.com/ubuntu/pool/main/libe/libemail-valid-perl/libemail-valid-perl_0.15-3_all.deb](http://fi.archive.ubuntu.com/ubuntu/pool/main/libe/libemail-valid-perl/libemail-valid-perl_0.15-3_all.deb)
Resolving proxyconf... 147.243.4.73
Connecting to proxyconf|147.243.4.73|:80... connected.
Proxy request sent, awaiting response... 404 Not Found
2010-07-29 12:31:16 ERROR 404: Not Found.

How I make the terminal to use the proxy.pac script rather than just proxyconf?

Any help would be appreciated as its been a while I am struggling with this.

Thanks in advance,
Siva

---

### Post by DaithiF on 2010-07-29
Hi, wget can't work directly with a .pac proxy file.  But its usually easy to just inspect that .pac file and set the http_proxy manually.  A .pac file contains a javascript function that for a given url returns the proxy address to use.  Often the function just returns a single proxy address regardless of the url.  Download the file and look for the line(s) that says return "PROXY someproxyaddress:port;" then set the http_proxy variable accordingly.  It should work unless/until the proxy address is changed, at which point you would have to do this process again.

---

