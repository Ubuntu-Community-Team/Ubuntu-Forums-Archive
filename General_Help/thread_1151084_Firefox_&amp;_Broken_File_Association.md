---
title: "Firefox &amp; Broken File Association"
date: 2009-05-06
forum: General Help
---

### Post by passonno on 2009-05-06
Hi,

So I just did a clean install of Jaunty, and I seem to not be able to open any downloaded files directly from firefox, when I click on the file in question in the download manager, I just get the "Launch Application" window with no applications listed.

Does anyone have a clue as to what's going on?

---

### Post by passonno on 2009-05-07
Bump

---

### Post by albinootje on 2009-05-07
> **passonno said:**
>  So I just did a clean install of Jaunty, and I seem to not be able to open any downloaded files directly from firefox, when I click on the file in question in the download manager, I just get the "Launch Application" window with no applications listed.


What kind of files are those, what are the extensions of those files ?

---

### Post by passonno on 2009-05-07
Any file at all. When I right click to open Nautilus, it is unable to even do that.

---

### Post by bodhi.zazen on 2009-05-07
Not sure ...

Open your firefox options and look in the application tab.

---

### Post by passonno on 2009-05-07
There are about 20 or so things listed in the content type tab under applications, and they all for the most part are multimedia codecs and files.  

And I can absolutely verify and replicate this issue, as this is the second time I have installed Netbook Remix with the same results.

Anyway, I am off to reinstall again, as the wireless is totally screwed, hopefully a reinstall will either reproduce the error(which would make it a bug)or fix it.

---

### Post by passonno on 2009-05-07
After a fresh install, I can indeed confirm that it does not work correctly in Netbook Remix.  I tried even deleting the entire .mozilla folder, and this of course did not help.

---

### Post by albinootje on 2009-05-07
> **passonno said:**
> Any file at all. When I right click to open Nautilus, it is unable to even do that.

But what are you comparing it with ? 

When I download a picture in Firefox on my Ubuntu Hardy desktop, I can double-click in the download window and then I can see the picture, but right click doesn't give me any "open with" options.
See attached screenshot.

---

### Post by passonno on 2009-05-07
You misunderstand.

When I, for example, download a .deb file, and then click to open, a "launch application" box opens up asking me to choose a helper application, and this box is empty.   Not only that, but I cannot even right click to open the folder in Nautilus.

---

### Post by passonno on 2009-05-07
I am beginning to believe that this is an issue with Jaunty UNR.  Can anyone confirm or deny that this is an issue in regular Jaunty?

---

### Post by passonno on 2009-05-07
I just ran the mozilla build straight from the website, and it works fine for me, so I believe that it's the Ubuntu particulars that are buggy.  Now how would I go about filing that bug report?

---

### Post by frederik.nnaji on 2009-09-18
i have the same problem, everytime i launch UNR from my usb-memorystick or from a fresh install:

it has no configured associations for any mime-types.

Jaunty Desktop would open say a .deb with gdebi, UNR doesn't know what application to use to open a freshly firefox downloaded .deb

this is a regular issue and should definitely be fixed.
for the gravity of this issue i would even suggest considering an immediate new release on the website with a new version number.. such as UNR 9.04.1 or so.

---

### Post by frederik.nnaji on 2009-09-18
> **passonno said:**
> I just ran the mozilla build straight from the website, and it works fine for me, so I believe that it's the Ubuntu particulars that are buggy.  Now how would I go about filing that bug report?

to fix the issue with the packaged firefox, obviously just simply select /urs/bin/nautilus as opening app

---

