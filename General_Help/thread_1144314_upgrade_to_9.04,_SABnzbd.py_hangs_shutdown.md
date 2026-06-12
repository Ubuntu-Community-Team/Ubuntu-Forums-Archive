---
title: "upgrade to 9.04, SABnzbd.py hangs shutdown"
date: 2009-04-30
forum: General Help
---

### Post by romeyde on 2009-04-30
I upgraded to 9.04 and ever since I was having issues shutting down.  I finally figured out that it was SABnzbd doing it.  If I kill it before shutting down, I have no issues.   The daemon runs as me.   Was thinking there was some sort of permission issue that for some reason wasn't an issue before upgrading?  Any idea how this would be resolved?

I thought I configured it to start via the old sessions, now startup applications, but not finding it there.

Here's the start string from it's init.d script:


/usr/bin/sudo -u $USERNAME -H python /usr/share/sabnzbd/SABnzbd.py -f /home/$USERNAME/.sabnzbd/sabnzbd.ini --browser 0 -d

---

### Post by sw1tch on 2009-04-30
Hi romeyde,

The hanging is due to a third party component of SABnzbd not being compatible with python 2.6 (which is now the default in jaunty). If you change "python" to "python25" in your init.d script it should work again.

Also SABnzbd is now available in the repository:
sudo apt-get install sabnzbdplus
sudo apt-get install sabnzbdplus-theme-smpl
sudo apt-get install sabnzbdplus-theme-plush

---

### Post by romeyde on 2009-04-30
> **sw1tch said:**
> If you change "python" to "python25" in your init.d script it should work again.


Thank you much for the reply, will give that a go.
For others with the same issue, note, it's python2.5 not python25.


Thanks again,
Derek

---

