---
title: "Custom thumbnailer no longer work in Gnome3"
date: 2011-11-15
forum: Desktop Environments
---

### Post by r_mano on 2011-11-15
Hi, I used to have custom thumbnailers on my system, see for example [http://rlog.rgtti.com/2010/11/28/adding-a-gnomenautilus-thumbnailer/](http://rlog.rgtti.com/2010/11/28/adding-a-gnomenautilus-thumbnailer/) 

Now the gconf configuration do not work anymore, so I searched a bit and found that the solution is adding a "gsetting schema", see for example [https://bugs.launchpad.net/ubuntu/+source/gnome-exe-thumbnailer/+bug/752578](https://bugs.launchpad.net/ubuntu/+source/gnome-exe-thumbnailer/+bug/752578) and [https://bugzilla.redhat.com/show_bug.cgi?id=636819#c29](https://bugzilla.redhat.com/show_bug.cgi?id=636819#c29)

I prepared a file in /usr/share/thumbnailers named xfig.thumbmailer, mode 0644, with the contents:

```

[Thumbnailer Entry]
TryExec=/home/romano/bin/xfig-thumb 
Exec=/home/romano/bin/xfig-thumb -s %s %u %o
MimeType=image/x-xfig;

```

But it still does not work. The script (xfig-thumb) *do* work, and the MIME type is correctly registered: 

```

(0)pern:~/education/AmplEle% xdg-mime query filetype feb09_1_1.fig
image/x-xfig

```

...so now I am stuck. Am I supposed to "register" the new thumbnailer someway? or restart something? (tried with nautilus, no joy).  

Do anyone know how to check/debug this thing? I mean, where I can find error codes or something like that?

---

### Post by r_mano on 2011-11-21
Ping?

---

### Post by r_mano on 2011-11-24
Ok, found by myself... 

It is the TryExec line that made the thing fail. So if I delete that line, all is (again) ok. Posted to my blog too, if someone wants the scripts. 

I will mark the thread solved; nevertheless, if someone can explain to me *why* it failed, I will appreciate that a lot.

---

