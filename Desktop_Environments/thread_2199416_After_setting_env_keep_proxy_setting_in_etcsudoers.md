---
title: "After setting env_keep proxy setting in /etc/sudoers sudo gedit no longer works"
date: 2014-01-13
forum: Desktop Environments
---

### Post by troywlsn on 2014-01-13
To get sudo apt-get working through my proxy server I have set 

Defaults env_keep="http_proxy https_proxy ftp_proxy" in /etc/sudoers after the line Defaults env_reset

This worked in getting my proxy settings to stay when running sudo apt-get. However, once I have added this line sudo gedit now fails. I get the error

** (gedit:3734): WARNING **: Could not open X display
cannot open display
Run 'gedit --help' to see a full list if available command line options

Note the error number changes each time I run it. If I run gedit without sudo it launches fine. also if I remove the Defaults env_keep line it works again. 

I realise I can do text editing with something other than gedit (i had to use nano to undo what I had saved into the sudoers file since gedit would no longer open as sudo), however I am worried there are other things that will break too.

Does anyone know how I can get sudo gedit working whilst also keeping the proxy settings in sudo? I am running Ubuntu 13.04. I have tried this on 2 separate machines, one running ubuntu outright, and the other within virtualbox on a mac.

Yours, 

Troy.

---

### Post by troywlsn on 2014-01-13
Problem solved

I also need to add in DISPLAY XAUTHORITY to the env_keep in /etc/sudoers and then it works

ie 
Defaults env_keep="http_proxy https_proxy ftp_proxy"
Defaults env_keep+="DISPLAY XAUTHORITY"

I found the solution here
[http://apurbapaul.blogspot.com.au/2012/10/adding-defaults-envkeep-in-visudo.html](http://apurbapaul.blogspot.com.au/2012/10/adding-defaults-envkeep-in-visudo.html)

---

