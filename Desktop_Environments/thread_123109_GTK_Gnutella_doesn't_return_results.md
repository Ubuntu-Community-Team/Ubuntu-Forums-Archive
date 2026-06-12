---
title: "GTK_Gnutella doesn't return results"
date: 2006-01-29
forum: Desktop Environments
---

### Post by chris_andrew on 2006-01-29
Hi,

I've just done a fresh install of Breezy, and installed GTK-Gnutella (one of my well used apps).  

When I search for items, no results are returned.

I can confirm that my network connection is good (i'm posting this).

Can anyone help?

Many thanks,

Chris.

---

### Post by lisa-m on 2006-01-29
dude same here, for some reason the gtk-gnutella is not connecting to the gnutella network, thus you get no results, i install 0.95-4 in breezy and the 0.96b latest version, and neither of them work. It's not your connection, it's either the program or the end server that connects you tot he server list fo gnutella networks world-wide. I hate fbi and i hate riaa and i hate mpaa, they never learn their lesson.

---

### Post by chris_andrew on 2006-01-29
lisa,

Thanks for that.  Anybody else got problems?

Thanks,

Chris.

---

### Post by lisa-m on 2006-01-29
you could try limewire for now, but i uses more ram cause of the java.

---

### Post by chris_andrew on 2006-01-29
Lisa,

Any recommendations from the standard repositories?

Cheers,

Chris.

---

### Post by Lambert on 2006-01-29
Same here, couldn't connect to gnutella network. I removed the version from the ubuntu repositories and downloaded from the sourceforge site (there's a .deb) and it works now for me.

Site seems to be down or  too busy at time of this posting though.

[http://gtk-gnutella.sourceforge.net/](http://gtk-gnutella.sourceforge.net/)

---

### Post by jimbo2150 on 2006-01-29
I would suggest:

**1)** Get latest version. 0.96 stable version is required at this point. Older versions will be disabled automatically.

Go to the site [http://gtk-gnutella.sourceforge.net/]("http://gtk-gnutella.sourceforge.net/").
Download the latest stable version (currently 0.96) with the .deb extension.

```
sudo dpkg -i /pathToFile/FileName.deb
```
The code above will unpack and install the latest version. NOTE: Sorry for not including the current file name. The site (sourceforge) is not letting me connect at the moment; the site may be down. **Remember to change */pathToFile/* and *FileName* to the current path holding the downloaded file and the name of the file respectively!**

**2)** Make sure your port is open!

Check your firewall. Gtk-Gnutella (by default) uses port 5122. Make sure your firewall (if you have one) is not blocking it. That includes firewalls built into routers!

**3)** Run the program (normally from **Applications->Internet->Gtk-Gnutella** menu).

For most people this should work, beyond that you may either be having internet connection problems or you may be blocked (packet shaping) by your ISP (Internet Service Provider). There are a few ISPs that block (or at least attempt to) file sharing programs.

---

### Post by chris_andrew on 2006-01-29
ATTENTION (From the GTK-Gnutella website):

24 January 2006, Version 0.96 Released

Version 0.96 is a stable release. It is now mandatory to use this version, since all previous versions have expired meaning they are going to be banned by all new gtk-gnutella clients and will no longer contact the Gnutella web caches.

Below is the changelog entry for the release, identifying the changes since the last stable version, 0.95.x.

Cheers,

Chris.

---

### Post by chris_andrew on 2006-02-05
Anybody know if the Ubuntu team has plans to address the release0.96 issue?

Thanks,

Chris.

---

### Post by annsachd on 2006-02-05
That would have been nice to know before I wasted the last half hour of my life.

Yeesh!

---

### Post by kperkins on 2006-02-05
I couldn't get gtk-gnutella to do a thing for me.  Far to difficult to set up.  I'm using Frostwire, and am quite happy with it.

---

### Post by chris_andrew on 2006-02-05
Hi,

Hmmm, it worked straight out of the box for me.  Never mind, 'horses for courses, etc'.  Thanks for the Frostwire suggestion.

Cheers,

Chris.

---

