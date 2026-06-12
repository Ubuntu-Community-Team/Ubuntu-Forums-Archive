---
title: "Amarok:  	 xml in the transferlist invalid + amarok won't build my collection"
date: 2009-01-06
forum: General Help
---

### Post by sam_thepeach on 2009-01-06
Okay, I'm new to kubuntu and the first thing I need to try and get working is my music, I have seen amarok and i think it's an awesome player, but it's only been giving me problems for a couple of hours now.

I can open my music files under the Files menu in Amarok, but when I tick the box where the files are stored and try to build the collection, I get a status bar that runs through to 100% but nothing appears in the collection.

I have tried to remove and re-install amarok but it doesn't work.

The behaviour is very eratic, for example, it gives me an error msg saying:

"xml In the transferlist was invalid"

but it doesn't give me that msg everytime.

Can anybody please help me, I just want to build the damn collection and listen to my music.

Please somebody help me?

---

### Post by Elfy on 2009-01-06
You don't say whether that is amarok or amarok2, from what I can see they deal differently with their databases - or at least they do here.

You say that you've removed and reinstalled amarok - did you also remove the config files?

Do 
```
sudo apt-get remove --purge amarok
```

Then open konqueror or whatever you use for your file manager and try and find the amarok config files, in gnome they are in ~/.kde/share/apps/amarok

```
konqueror ~/.kde/share/apps/amarok
```

If they are there delete them.

Then reinstall amarok

```
sudo apt-get install amarok
```

---

### Post by sam_thepeach on 2009-01-06
Apologies, I am using Amarok2.

Thank you so much for the help. It worked, I see my collection now.

The learning curve for kubuntu is quite steep, but it's fun and this software is way more effective than anything else.

Thank you again!!

Regards:popcorn:

---

### Post by Elfy on 2009-01-06
You're welcome.

Wasn't sure that path would work for amarok2 - seem to be in a differnt place here.

---

