---
title: "Openbox: starting Nautilus brings up Gnome desktop"
date: 2011-08-30
forum: Desktop Environments
---

### Post by intheflesh on 2011-08-30
I installed and configured Openbox on top of Ubuntu 11.04. I'm pretty happy how it turned out, but there's this annoyance when I start Nautilus, either from Openbox' menu, or, when I download a file and want to open it from Firefox. I read here that Thunar might be the problem so i removed it, and now I don't get a "Location is not a folder" error message, but still get the same Gnome desktop popping up as usual.

How do I at least stop Gnome desktop from starting, or even better, how do I completely switch to Thunar in Openbox?

---

### Post by mcduck on 2011-08-30
Just make sure you are starting Nautilus with "nautilus --no-desktop" and it won't take over the desktop.

Similar thing with Thunar, if you don't want tit to draw desktop for you then you need to disable that in Thunar's options.

---

### Post by intheflesh on 2011-08-30
Okay, thanks for the info. I can change it in Openbox menu, but everywhere else it will remain the same. Can I change the default behaviour but just for Openbox?

Now if I install Thunar again I'd get the same hassle as before (aparently, it depends on exo-utils which are causing the problem). Is there anything I can do to make Thunar my main file manager on Openbox, and keep Nautilus for Gnome?

---

### Post by mcduck on 2011-08-30
> **intheflesh said:**
> Okay, thanks for the info. I can change it in Openbox menu, but everywhere else it will remain the same. Can I change the default behaviour but just for Openbox?

Now if I install Thunar again I'd get the same hassle as before (aparently, it depends on exo-utils which are causing the problem). Is there anything I can do to make Thunar my main file manager on Openbox, and keep Nautilus for Gnome?

I'm not sure what hassle you are talking about. :D

Anyway, using Thunar for Openbox and Nautilus for Gnome works just fine. It's just that whichever file manager you want to use, you need to tell that filemanager to not manage the desktop (unless you want it to do that). Using Thunar won't cause Nautilus to take over any desktop, and same of course goes the other way.

Also I don't think there's any way to configure programs to behave differently on different desktop environments, so no, you can't for example make Firefox use Nautilus in gnome and Thunar in Openbox. You'd have to make different user accounts for each DE for that to work. (or alternatively just stop opening file manager windows through your web browser, I never do that so I can happily run Nautilus as my file manager in OB as well. ;))

---

### Post by Kexolino on 2011-08-30
I don't know if this will help (maybe you've already done it), but you can give it a go, post the result back here.

Open gconf-editor, then navigate to Apps > nautilus > preferences, and untick the show_desktop line.

---

### Post by kartabosh on 2011-08-30
i use thunar with openbox
you don't really need to install anything 
whenever you need a file manager open thunar

---

### Post by intheflesh on 2011-08-30
@[Kexolino]("http://ubuntuforums.org/member.php?u=1107869"): Well, I did what you asked and reinstalled Thunar. Now the Gnome desktop doesn't show up (yay, no more killall nautilus), but still when I want to open a downloaded file I get the same error (for example: Could not display "/home/vladimir/Desktop/httpd-2.3.14-beta.tar.gz". The location is not a folder.) and then it just opens my home folder in Nautilus. Open containing folder works (again opens it in Nautilus). But thank you, I owe you one. 

@[kartabosh]("http://ubuntuforums.org/member.php?u=1051080"): I know, I do that to, it's just this annoying thing with Firefox (so far; haven't tested it on Chromium yet).

---

### Post by mcduck on 2011-08-30
> **intheflesh said:**
> @[Kexolino]("http://ubuntuforums.org/member.php?u=1107869"): Well, I did what you asked and reinstalled Thunar. Now the Gnome desktop doesn't show up (yay, no more killall nautilus), but still when I want to open a downloaded file I get the same error (for example: Could not display "/home/vladimir/Desktop/httpd-2.3.14-beta.tar.gz". The location is not a folder.) and then it just opens my home folder in Nautilus. Open containing folder works (again opens it in Nautilus). But thank you, I owe you one. 

@[kartabosh]("http://ubuntuforums.org/member.php?u=1051080"): I know, I do that to, it's just this annoying thing with Firefox (so far; haven't tested it on Chromium yet).

The error message makes sense, Thunar is a file manager, it's not capable of *opening* files. If you wish to open files directly from the browser you'll need to choose a program that actually can handle the file type you want to open, image viewer for image files, archive manager for archives and so on.

(as a tip, using *xdg-open* as the program might work in many cases, it opens a file in the configured default application for that file type. Although it of course doesn't support every possible type of files)

---

### Post by Kexolino on 2011-08-30
Ultimately you can set Thunar to be the default with 

```
sudo update-alternatives --all
```

Just press enter until you get the option with the two file managers, and select Thunar. As far as I know, if you set the default file manager in Gnome, it doesn't affect Openbox. That might be the problem.

---

### Post by intheflesh on 2011-08-31
So it turns out the problem only occurs in Firefox. Chromium opens files with no hassle. Thank you all for your support, I'll see to straighten out the misbehaving browser.

---

