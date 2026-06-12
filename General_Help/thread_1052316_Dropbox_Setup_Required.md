---
title: "Dropbox Setup Required"
date: 2009-01-27
forum: General Help
---

### Post by Rytron on 2009-01-27
Hi. I need a setup guide for Dropbox. I downloaded the Ubuntu version from the [Dropbox homepage]("https://www.getdropbox.com/home").

---

### Post by argraff on 2009-01-27
It's easier than it appears - had some trouble myself. Once you have the .deb file downloaded, go back to the dropbox website and make yourself a login. The rest won't work without a login.

Once you have a login, double-click the .deb file and let it install. Then you will have a folder in your home directory called "Dropbox." Put stuff in there and it will start uploading it to Dropbox in the background.

Hope that helps!

---

### Post by Rytron on 2009-01-27
> **argraff said:**
> It's easier than it appears - had some trouble myself. Once you have the .deb file downloaded, go back to the dropbox website and make yourself a login. The rest won't work without a login.

Once you have a login, double-click the .deb file and let it install. Then you will have a folder in your home directory called "Dropbox." Put stuff in there and it will start uploading it to Dropbox in the background.

Hope that helps!

Thank you argraff. I was just about to post that. I downloaded the deb package earlier today. Then installed it. As you said I signed in and a while later the dropbox was in the notification area.
Cheers.

:popcorn:

---

### Post by Andavane on 2009-02-09
> **argraff said:**
> It's easier than it appears - had some trouble myself. Once you have the .deb file downloaded, go back to the dropbox website and make yourself a login. The rest won't work without a login.

Once you have a login, double-click the .deb file and let it install. Then you will have a folder in your home directory called "Dropbox." Put stuff in there and it will start uploading it to Dropbox in the background.

Hope that helps!
Hello:
Can we go through again?
I have downloaded it on to the desktop, double-clicked and it's installed.
Now what? I can't find it anywhere.

looking forward to a reply.

Regards

John

---

### Post by JJErtai on 2009-02-09
This just happened to me-

Try opening a terminal and typing:
sudo nautilus

That should open nautilus as root. When I did this, a dropbox icon appeared on the top panel. Click that then >start dropbox. It should start downloading. When done it'll run, enter your email address and p/w and it should be set up!

---

### Post by JJErtai on 2009-02-09
After installing (both the stable version and the 448 version) neither will connect to the server online. Clicking "Start Dropbox" does nothing. The only way it connects is if I open a terminal and type:

sudo nautilus

allowing nautilus to run with root permissions. Then it will connect, download the files it needs and work... until I close that nautilus window/restart the computer. So I guess not fixed after all, any ideas?

---

### Post by JJErtai on 2009-02-09
Solution: Make sure both your "Dropbox" and ".dropbox" folders (and files within them) are set to be owned by your username, not root.

That should help fix this issue. :)

---

### Post by Andavane on 2009-02-09
Well gentlemen:
I spent all of yesterday trying to get it to work and then part of this morning.
Then I had to go out.
When I returned, Iturned on the Intrepid machine,in order to try again and lo and behold, the "Welcome to DropBox" thingie popped up and ran me through its questionnaire.

So far it seems to be working fine... although not sure whether it will support the level of folders I have in my files.

Will study about sharing next....

A bit weird this...

Regards

John

---

