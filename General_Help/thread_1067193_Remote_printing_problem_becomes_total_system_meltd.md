---
title: "Remote printing problem becomes total system meltdown - can't even login"
date: 2009-02-11
forum: General Help
---

### Post by jamespetts on 2009-02-11
At home, there are four computers: study, bedroom, kitchen and parlour. Kitchen and parlour are running Ubuntu Intrepid; bedroom is running Ubuntu Hardy and Study is running Windows XP.

Earlier this evening, a problem was found printing from kitchen to parlour. I had earlier configured cups using the GUI to print from kitchen to parlour without difficulty, so found this odd. I spent a great deal of time trying to solve the problem without success, the problem always appearing to be that the server was refusing permission to access it to the clients, even though the server was configured to allow remote printing and remote administration, the clients' IPs were in the allowed list, all relevant usernames were given permission to print, and it had worked with those exact settings recently before. 

I tried to configure the printer from bedroom (I had not previously set up the printer from there), and got exactly the same error. I tried to access the CUPS web configuration on parlour, from bedroom and I got a 403 (I had earlier tried the same from kitchen with the same result). So, on bedroom, I tried to configure the printer through Bedroom's CUPS web interface. I added a printer, and selected the appropriate driver (HP Photosmart D7300 series). I sent it a test page from the web interface, but nothing printed - it was marked perpetually as "processing".

I went to parlour to investigate, and could now not access the CUPS web interface even locally - it appeared that the web server was not giving any sort of response. I tried restarting CUPS from the command line, but got a segmentation fault. Trying to reboot from the command line also gave a segmentation fault. I rebooted from the GUI. The loading bar screen appeared, but there were bizarre artefacts (looking like fragments of the blank loading bar under the Ubuntu logo) next to the live loading bar, which progressed as normal.

I reached the login screen as normal, but any attempt to login just brought the interface back to the login screen again, even with "failsafe terminal" selected as the session. I tried rebooting in failsafe mode from the GRUB menu, and attempted to use the automatic repair tools there (FSCK, XFIX, and DPKG fix), but, on rebooting again, there was no change. I am at a total loss, and very concerned that something quite drastic but utterly incomprehensible has gone wrong. I cannot even access shared NFS folders on parlour from other computers. I should be very, very grateful for any assistance at all, especially as this is my parents' computer that I help to maintain for them and they really do rely on it for a great many things.

---

