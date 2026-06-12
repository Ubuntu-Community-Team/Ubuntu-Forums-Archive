---
title: "Replacement for Evolution?"
date: 2005-03-25
forum: Desktop Environments
---

### Post by chz on 2005-03-25
Anybody know of any good app thats relative to evolution (mail/calendar/tasks). I need something with good import/export features (evolution only imports) and something that can do it in CSV (which evolution doesnt do). I looked at thunderbird which i love as a mail client, but i would like an all in one application. If anybody knows of calendar/task apps that run well with thunderbird, please let me know. Thanks =)

---

### Post by kb00heda on 2005-03-25
You can use Thunderbird with a calendar. It's an easily installed extension. This worked for me when I tested:

1) download the calendar extension for Linux from

[http://www.mozilla.org/projects/calendar/download.html#download_thunderbird](http://www.mozilla.org/projects/calendar/download.html#download_thunderbird) 

by right-clicking the link and choosing "Save Link As...";

2) start Thunderbird (I assume you have it installed already --- otherwise it's done in the twinkling of an eye through apt);

3) navigate via "Tools --> Extensions --> Install" and choose your recently downloaded calendar (xpi-file);

4) restart Thunderbird to find the calendar under "Tools --> Calendar".

Hopefully that fulfills your needs!

I believe Mozilla has a standalone calendar as well, named Sunbird, but you get the same deal here, via the Thunderbird extension.

/David

---

### Post by mariuss on 2005-04-27
Is there a way to start the Mozilla Calendar at startup if it is installed as a Thunderbird extension?

I find this being a major problem, you would want your calendar to autostart so you get the notifications.

---

### Post by mariuss on 2005-04-27
I found the solution, just run:
```
mozilla-thunderbird -mail -calendar
```

The only problem I have found with this approach is that if you use a tray minimazing application to run Thunderbird like this then it will get confused by the two windows and it will not create proper tray icons for both.

Marius

---

### Post by Sweezel on 2005-07-10
FYI - I just exported my Evolution Contacts to a vcf (vcard file) and converted it to ldif and several forms of csv. It actually took several days to figure it out, but heres how I finally did it.


Select all of your contacts in Evolution and click "save as Vcard" in the Evo "File" menu. Convert your file to several different formats using "VCF-Convert" at [http://labs.brotherli.ch/](http://labs.brotherli.ch/).

It was the only way I could get all of my contacts imported into Palm Desktop. This utility worked better than /usr/lib/evolution/2.2/evolution-addressbook-export or "Dawn".


LOL

---

### Post by filemanager on 2005-07-11
Does anyone know how to convert a CSV into something Evolution can import?

---

