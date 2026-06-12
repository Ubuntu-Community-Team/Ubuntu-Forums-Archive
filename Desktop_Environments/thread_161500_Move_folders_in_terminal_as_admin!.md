---
title: "Move folders in terminal as admin!"
date: 2006-04-17
forum: Desktop Environments
---

### Post by Mr Egg on 2006-04-17
Hello. I was trying to upgrade to Firefox 1.5.0.2 and I accidentally deleted Firefox from wherever it was installed. I download the .tar.gz file and ran the BIN file, so I'm using that to post this message, but I want to install it like it should have been. So I'm thinking I should just copy these files to wherever they should be. First, can anyone tell me where it should be installed, and second can anyone tell me how I can copy these folders across in Terminal.

Thanks in advance.

---

### Post by xenmax on 2006-04-17
I also dowload tar.gz from firefox website and untar them to a location.
if i do which -a firefox, i get (this is from memory; away from my ubuntu m/c ATM)
```
/usr/bin/firefox
/usr/bin/X11/firefox.

``` However, they are both links. And second one might be a hard-link - i dont touch it and it still gets updated. To fix your /usr/bin/firefox,
try
```
cd /usr/bin
sudo ln -s /path/to/firefox-1.5.0.2/firefox firefox
``` 
If /usr/bin/firefox exists (shouldn't be from what you have told), use ln -sf

Hope this helps.

EDIT: where /path/to/.... is path to where firefox executable is extracted to from tar.gz

---

### Post by jrib on 2006-04-17
take a look at [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

