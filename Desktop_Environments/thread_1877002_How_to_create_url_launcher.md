---
title: "How to create url launcher?"
date: 2011-11-07
forum: Desktop Environments
---

### Post by wah fun on 2011-11-07
I am trying to create a panel launcher that will access the Amazon seller account login page however, the address is so long the launcher doesn't work correctly.  In the launcher I have the following on the command line:

firefox [https://www.amazon.com/ap/signin?_encoding=UTF8&openid.assoc_handle=usflex&openid.return_to=https%3A%2F%2Fwww.amazon.com%2Fgp%2Fseller-account%2Fmanagement%2Fyour-account.html%3Fie%3DUTF8%26ref_%3Dya_2&openid.mode=checkid_setup&openid.ns=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0&openid.claimed_id=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select&openid.pape.max_auth_age=900&openid.ns.pape=http%3A%2F%2Fspecs.openid.net%2Fextensions%2Fpape%2F1.0&openid.identity=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select](https://www.amazon.com/ap/signin?_encoding=UTF8&openid.assoc_handle=usflex&openid.return_to=https%3A%2F%2Fwww.amazon.com%2Fgp%2Fseller-account%2Fmanagement%2Fyour-account.html%3Fie%3DUTF8%26ref_%3Dya_2&openid.mode=checkid_setup&openid.ns=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0&openid.claimed_id=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select&openid.pape.max_auth_age=900&openid.ns.pape=http%3A%2F%2Fspecs.openid.net%2Fextensions%2Fpape%2F1.0&openid.identity=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select)

However, when the launcher is opened, the page is not opened and instead an error page is opened with the following message:

	
Looking for Something?
We're sorry. The Web address you entered is not a functioning page on our site
Go to Amazon.com's Home Page

Now, I know the address is correct because I can open it from within Firefox. In fact that's where I copied the address for the launcher.

I know that I can use redirect services like tiny url but I prefer not to do that. So, has anyone had this problem and resolved it? If so, I would like to know how you did it.

Thx.

ubuntu 10.04 LTS

---

### Post by tors on 2011-11-07
Try to enclose the address within ""

firefox "the url"

---

### Post by wah fun on 2011-11-07
thx but that didn't work either.

I know this is tacky but I can create the launcher in windows xp panel. So I am not sure it is the length of the url.

---

### Post by mc4man on 2011-11-08
A launcher is a .desktop where the command is on the Exec= line
The issue with your url is't the length, likely the %'s in it. They don't work well in an Exec=

What you can do is create a simple script to launch FF on the url & use the scriptname or **if where you place the isn't in your path** then the /full/path/to/scriptname on the Exec= line in the launcher (.desktop

I believe 10.04 will auto add a ~/bin after a restart so 1st. try like this (I use 11.10, things are a bit different

```
mkdir -p ~/bin; gedit ~/bin/amazon1
```

Copy & Paste this into gedit, then save & close gedit 
(get the whole line, it's long
```
#!/bin/bash
firefox "https://www.amazon.com/ap/signin?_encoding=UTF8&openid.assoc_handle=usflex&openid.return_to=https%3A%2F%2Fwww.amazon.com%2Fgp%2Fseller-account%2Fmanagement%2Fyour-account.html%3Fie%3DUTF8%26ref_%3Dya_2&openid.mode=checkid_setup&openid.ns=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0&openid.claimed_id=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select&openid.pape.max_auth_age=900&openid.ns.pape=http%3A%2F%2Fspecs.openid.net%2Fextensions%2Fpape%2F1.0&openid.identity=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select"
```

then in the same terminal run this command
```
chmod u+x ~/bin/amazon1
```

Probably best to create the launcher here, then you can drag onto your panel. (can be created on Desktop if you wish instead
Because I'm not sure this dir. exists will add a command to check & create if not there, probably is
Below is one complete command C&P the whole code box

```
mkdir -p ~/.local/share/applications; \
gedit ~/.local/share/applications/amalogin.desktop
```

Copy & paste this in, feel free to change the Icon= line, some icons can be name only, some need /full/path/to/icon.png. Also feel free to change the Name= (display name of launcher

```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Exec=amazon1
Name=Amazon Sellers
Icon=apple-green
Categories=GNOME;GTK;Network;WebBrowser;
```

Save & close out gedit, then 
```
chmod u+x ~/.local/share/applications/amalogin.desktop
```

Now navigate to the location & drag onto panel 
```
nautilus ~/.local/share/applications/
```

You now need to **do a restart** to add ~/bin to your path, if it is all should work fine

---

### Post by wah fun on 2011-11-10
mc4man THANK YOU! It works perfectly. I so appreciate your help and knowledge and the time you spent creating and showing me the commands. I am still learning linux so I am going to study all these commands so I can understand exactly what they do. Perhaps someday I will be able to help some other linux user in a similar way.

Oh, by the way, I am running xubuntu 11.10 as a guest in virtualbox and this works there as well.

---

