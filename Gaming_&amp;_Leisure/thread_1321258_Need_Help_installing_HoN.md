---
title: "Need Help installing HoN"
date: 2009-11-09
forum: Gaming &amp; Leisure
---

### Post by Blakio on 2009-11-09
Well I am not very technically inclined when it comes to dealing with files and such. I can do a few little things on the computer but I am having trouble installing Heroes of Newerth. I downloaded it but I am confused as to what to do next. I have googled it and have not  been able to figuree it out...not much info since its only in Beta. So can any one help me?

---

### Post by DreDub on 2009-11-10
Basically you have to enable execution of the .sh file you downloaded.

open up a terminal and cd to the directoy you downloaded HoN to, then:

```
chmod +x HoNClient-0.1.41.sh

./HoNClient-0.1.41.sh
```That will launch the installer, then just go click through that.

---

### Post by Blakio on 2009-11-10
Ok I'm fairly certain I am opening the cd right but  its telling me there is no such file directory, also I put all that code into the terminal right? Sorry, if I sound like a not so smart person I am really trying to understand this. Thank you for your help.

---

### Post by Perfect Storm on 2009-11-10
Make sure you're in the right directory.

Eg. on your Desktop

```
cd ~/Desktop
```

Also check if the installation script have a different name than shown by DreDub.

---

### Post by Blakio on 2009-11-10
Ok I was making more complicated than i needed to. I figured it out. thx a ton

---

### Post by Vadi on 2009-11-10
Yeah, people are making it more complicated than it is.

Set the file so you can run it - do that by right-clicking on it, select properties, and enable that in the permissions tab.

Then just double-click to run it.

---

