---
title: "Brother printer on windows"
date: 2009-01-26
forum: General Help
---

### Post by BETELGEUSE58 on 2009-01-26
Hi. I have Kubuntu, the newest version. I am trying to add a network printer, a brother hl-2140 on my xp machine. I think it may not be finding it because of a firewall on kubuntu. Does kubuntu have a firewall and if so what is its name, where is it? Any other suggestions welcome. I also want to mount a drive on the windows desktop to this kubuntu desktop but I'll keep searching for that. 
Thanks.

---

### Post by hyper_ch on 2009-01-26
kubuntu has a firewall, it's name is iptables and by default it has no rules in it which equals that it lets everything pass. So it's not the firewall that's the issue here.

Sounds like you sharing the printer from WinXP (so it's not really a network printer) and you will need to install samba to access it.

---

### Post by BETELGEUSE58 on 2009-01-26
Ok Thanks. I'll try that. I thought samba was already installed but I'll check it out.

---

### Post by BETELGEUSE58 on 2009-01-26
Installed parts of samba that werent installed if that makes any sense. Still cant find printer. I can access shared drive on same computer as printer, and I have printer as a network printer from within windows on this dual boot laptop. Any other suggestions?

---

### Post by mb_webguy on 2009-01-26
Is this an actual network printer, or is it a printer attached to another computer on the network?

If it's the latter, can you see the computer in Places->Network (or the Kubuntu equivalent thereof)?

---

### Post by BETELGEUSE58 on 2009-01-26
Hi. Its a printer attatched to a computer on the network(an xp computer). I can see it (the computer) from places / network / samba shares

---

### Post by mb_webguy on 2009-01-26
Ok, so when you go to Adminstration->Printing, click "New", select "Windows printer via Samba", and click the "Browse" button, can you not find the printer?

If not, are you sure you're sharing it from the Windows computer?

---

### Post by BETELGEUSE58 on 2009-01-26
Its a little different in Kubuntu, but when I go to printing, windows printer via samba    there is no option to browse for one, it wants the smb:// address. It is definitely shared because I also have windows on this computer and can print from it here while in windows.

---

### Post by mb_webguy on 2009-01-26
Can you not browse the network, go to the computer to which the printer is connected, and get the smb address that way?

---

