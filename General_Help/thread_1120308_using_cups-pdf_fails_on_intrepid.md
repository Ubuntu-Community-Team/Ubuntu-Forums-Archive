---
title: "using cups-pdf fails on intrepid"
date: 2009-04-08
forum: General Help
---

### Post by Polygon on 2009-04-08
I followed the instructions here to create a pdf printer:

[http://hydtech.wordpress.com/2009/03/17/how-to-print-to-pdf-in-ubuntu-intrepid-ibex-and-jaunty-jackalope/](http://hydtech.wordpress.com/2009/03/17/how-to-print-to-pdf-in-ubuntu-intrepid-ibex-and-jaunty-jackalope/)


except it doesn't work. it appears to work but it just doesn't produce a file. I am noticing in my messages log:

```
Apr  8 18:04:15 Humboldti kernel: [ 4720.251263] type=1503 audit(1239239055.634:10): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=8212 profile="/usr/sbin/cupsd"
```

so...somewhere it doesn't have permissions. Any idea on what i need to do? =/

---

### Post by 3Miro on 2009-04-08
Where are you trying you trying to save the file. It should be saved in Documents or something like it.

I thought pdf printing is enabled by default, it works fine for me without any special settings.

---

### Post by Polygon on 2009-04-08
print to file doesn't work on everything, since it is not an actual printer...what cups-pdf does is make a virtual printer that everything can use.

---

### Post by TasogareNoKagi on 2009-04-09
I got a similar message in xconsole when trying to use the PDF printer ... it pointed me at /usr/lib/cups/backend/cups-pdf, which I noted had permissions set to 700.  I ran the following

```
sudo chmod a+rx /usr/lib/cups/backend/cups-pdf
sudo chmod +s /usr/lib/cups/backend/cups-pdf
```

and afterwards printing worked.  Since the error message you're getting is different from mine, you may need to poke at a different file.

---

