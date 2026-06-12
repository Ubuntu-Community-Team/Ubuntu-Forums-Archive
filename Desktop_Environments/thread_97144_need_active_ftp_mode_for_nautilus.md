---
title: "need active ftp mode for nautilus"
date: 2005-11-30
forum: Desktop Environments
---

### Post by fdimmling on 2005-11-30
How can I make nautilus use active ftp mode instead of passive mode? 

Friedrich

---

### Post by thegnark on 2005-11-30
erm, what?

AFAIK, PASV is used when you're behind a firewall - and there's not much you can do about it.

---

### Post by fdimmling on 2005-11-30
[QUOTE=thegnark]
AFAIK, PASV is used when you're behind a firewall - and there's not much you can do about it.[/QUOTE]

Unfortunately my new provider does not allow PASV. I have checked it by lftp: using PASV there is no connection, disabling PASV it works. Despite the firewall of my DSL router active ftp seems to work.

Friedrich

---

### Post by hedge on 2005-12-02
[quote=fdimmling]Unfortunately my new provider does not allow PASV. I have checked it by lftp: using PASV there is no connection, disabling PASV it works. Despite the firewall of my DSL router active ftp seems to work.

Friedrich[/quote] 
I have yet to find the setting in gnome however if you must have it, in KDE you can get port mode to be the default for Konqueror. by K>Preferences>Internet & Networking>Connection Prefrences and uncheck (x) enable passive mode (PASV).

Work around for gnome if you have shell access to the server instead of establishing the connection using login ftp, try ssh. But any html editors that you use like NVU will still be needing the passive mode for any site manmagent functionality.

Then again if you have shell access, and the server is a Red Hat or Fedora linux box you can enable port mode on the server by adding the port range to the /etc/sysconfig/iptables.

hope this helps

hedge

---

### Post by sabitha on 2005-12-02
how to make nautilus don't ask me pasword if i browse my samba network like hoary before .
:KS now im using brezzy

---

### Post by OliW on 2007-11-15
Have you had any luck with this? I'm having the same problem.

---

### Post by OliW on 2007-11-18
I found a way around this... It's a long way around, but it works: you can mount active ftps with curlftpfs. There are several tutorials knocking about and they all seem to do the same thing.

---

### Post by fdimmling on 2007-12-03
> **OliW said:**
> I found a way around this... It's a long way around, but it works: you can mount active ftps with curlftpfs. There are several tutorials knocking about and they all seem to do the same thing.

My solution is to use gftp.

Friedrich

---

### Post by dolson on 2008-01-12
I searched all over the net for a solution to this Nautilus issue and found no answer. Well, my issue is that I needed passive mode support, so it's technically the opposite, but the solution should be the same process, but in reverse.

However, I actually figured it out on my own... I mean, it works for me - try it for yourself and if it doesn't work, then I guess it's just a fluke.

sudo vim /etc/Net

Find the line that says:

        ftp_ext_passive => 0,

and change it to:

        ftp_ext_passive => 1,

Save the file, give it about 5-10 seconds, and then try Nautilus again.

I did this and Nautilus no longer hangs, it actually shows my files. I tried reversing it, and Nautilus reverted back to it's old ways... So I'm sure this is the solution.

Note: I am using debian, not Ubuntu, so maybe it's different, but I figured they're similar enough that it might be the solution you guys are after.

---

### Post by SanskritFritz on 2008-03-15
> **dolson said:**
> ftp_ext_passive => 1,
Save the file, give it about 5-10 seconds, and then try Nautilus again.That didn't work here. Anyone has a solution please? I can connect via command line ftp in passive mode, but not in active mode (firewall being the reason). I really want to use Nautilus for ftp.

---

### Post by SanskritFritz on 2008-03-16
Bump. Please, can I enable passive mode for ftp in Nautilus? Or alternatively, can I mount an ftp server somehow?

---

