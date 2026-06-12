---
title: "How Do I UPDATE Fusion"
date: 2007-08-14
forum: Desktop Effects &amp; Customization
---

### Post by shaan.mi on 2007-08-14
Hi, I was just wondering, how do I update fusion to 0.5.2 ? I am currently using 0.4  on fiesty!  0.5.2 was released and its not coming through my update manager. Is there a way to manually update it myself ? Thanks!

---

### Post by steveneddy on 2007-08-14
You will have to uninstall the older version and DL the new version, compile it for your machine, then install it.

Why don't you just use Trevinio's Repository? It will have the updated Fusion soon, and it will update when it comes across.

---

### Post by misfitpierce on 2007-08-14
Usually whereever you got your compiz fusion from the repository will update and show you an update for it. Im not sure what repos. are out there for it but some may take onger than others to give update. Perhaps the Trevinos as stated is a good repository to add to computer and it should notify when update is avail.

---

### Post by steveneddy on 2007-08-14
[Here's the link]("http://forum.compiz-fusion.org/showthread.php?t=1012") to Trevinio's repo's

Here's Trevinio's key (run in terminal)

```

sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -

```

After installing - copy this script and put it in your Home folder - 

```

#!/bin/sh

# click to start, click to stop

if pidof compiz.real | grep [0-9] > /dev/null
then
 exec metacity --replace
else
 exec compiz --replace -c emerald

fi

```

Name it fission,

Then make a launcher for your desktop or toolbar

in the launcher - to launch the script - browse for your script in the Home folder.

Use the icon provided here.

Good as gold. Now go use it and have fun.

---

