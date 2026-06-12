---
title: "Konqueror always opens debs in KWrite"
date: 2007-03-17
forum: Desktop Environments
---

### Post by clintonthegeek on 2007-03-17
Hey everyone,

I'm having a hell of a time with Kubuntu file associations. It seems that every time I click on a link to a .deb, Konqueror either automatically opens the file with KWrite, and then complains about it being a binary file (duh), or loads the deb in KWrite *in* my Konqueror frame, *then *complains about it being binary.

Lately I've been getting around it using right-click and Save Link As..., but lots of sites use php redirects, so there are no links to the actual file (the latest offender being [the GIMPshop download page]("http://www.gimpshop.com/download.shtml")), and it becomes a pain to actually get my file (I end up using wget).

So, figuring it defaulted to KWrite 'cause debs have no file association to any program, I downloaded and installed KPackage, and associated debs with it. I also noticed that the box "Ask _w_hether to save to disk instead" was already checked, so Konqueror *should* have been asking me to save the deb somewhere *anyways*.

Well, it didn't work, debs still open in KWrite, and I've had to copy/paste the URL from the KDE File transfer dialogue, and wget it again to get my stupid GIMPshop deb. ](*,)

Any help would be much obliged!

-Clinton

---

### Post by GiantRobot on 2007-03-17
I believe the easiest thing to do it to right-click on the *.deb, find the 'open with' section and choose KPackage.

It should be like by default in Kubuntu since I haven't changed anything and thats the way it is in my installation.

Good Luck!

---

### Post by clintonthegeek on 2007-03-17
Thanks for the reply,

The thing is, *getting* the deb is a pain in the butt. Clicking on a link in the webpage should ask me where to save it, or at least open it in KPackage, but instead always tries to open it in KWrite.

Once I figure a way to actually download the file, then opening with KPackage would be fine.

Actually, you reminded me that I saved parts of my .kde folder from my old desktop (Mepis), to save time resetting all my KDE settings in Edgy, perhaps I copied over some wonky settings of mine. But it shouldn't be an issue if the File Association dialogue actually *did it's job*! :p

-Clinton

---

### Post by ecoxmit on 2007-06-07
Actually, I am having the same problem. 

Php links are automatically opened with Kate (or Kwrite), and when trying to "Save As..", the are saved with the wrong filename (i.e. "blahblah.php") instead of the linked filename. Really a pain. 

Anyone knows how to fix this?

(I got this under kubuntu, after installing from ubuntu)

---

### Post by clintonthegeek on 2007-08-14
Yup, that's it. For an example to try out, everyone try going to 

[http://www.frostwire.com/download/?os=ubuntu](http://www.frostwire.com/download/?os=ubuntu)

in Konqueror, and try downloading Frostwire for Ubuntu. The link goes to a PHP script which directs the browser to the file. But, it doesn't give me a download dialogue, or anything of the like -- it opens it in Kate. I can't Save As... or wget the link, or else I just save some weird php file.

The only way I've worked it out is to hurry up and copy/paste the real url from the file download window, and wget that. But that's a major PITA.

debs are configured to open with kpackage, to open a dialogue, to view in external viewer, etc. and yet it has no effect.

No ideas? Should I file a bug-report?

---

### Post by rakku-toki telkio-kuuni on 2007-08-25
I have the same problem, so I suppose you can report it.

My workaround is simple: I download with KGet and change the name of the download from "download.php" to "whatever.deb" - surprisingly, it works.

---

### Post by Erunno on 2007-08-25
> **clintonthegeek said:**
> [http://www.frostwire.com/download/?os=ubuntu](http://www.frostwire.com/download/?os=ubuntu)

I tried to download FrostWire under openSUSE 10.2 with kget and it worked flawlessly so I guess that must be a Kubuntu (mis)configuration.

---

### Post by ecoxmit on 2007-08-25
Indeed

Having Kget installed thus seems to solve the problem for me

---

