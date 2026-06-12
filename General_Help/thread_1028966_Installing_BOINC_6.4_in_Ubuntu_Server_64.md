---
title: "Installing BOINC 6.4 in Ubuntu Server 64"
date: 2009-01-02
forum: General Help
---

### Post by california-ken on 2009-01-02
I can´t get the newest version of BOINC to run properly under Ubuntu Server 64 bit.  I downloaded the ¨.sh¨ file and extracted it to my home directory.  From the terminal, I ran the ¨run_client¨ and ¨run_manager¨ files in the newly created BOINC folder.  The BOINC manager loaded but would not connect to any clients.

Prior to the version 6.4 download, I used the Gnome Applications/Add & Remove programs to install BOINC.  It installed BOINC Version 6.2.12 (beta) which runs, connects to clients but does not show any graphics or supply a screen saver.

I am not very experienced with Linux or Unbuntu.

Can anyone help me get BOINC 6.4 running under Ubuntu Server 64?  The BOINC web site says 6.4 should be trouble free and show graphics with Linux 32 and 64 bit systems.

Thanks.

Ken

---

### Post by ju2wheels on 2009-01-03
Save yourself the headache and always look for .deb installers first...

[http://www.getdeb.net/app/Boinc](http://www.getdeb.net/app/Boinc)

Enjoy, I use it on my Intrepid 64bit, just wish I had the nvidia 180 drivers so I can have my video card do some crunching too but im too lazy to do that myself...

---

### Post by california-ken on 2009-01-03
Thanks for the reference to the getdeb site.  I downloaded the Boinc client and manager ¨.deb¨ files, placed them into an new folder in my home directory and extracted them and the ¨.gz¨ files they contained into the same folder.

I don know what to do next.  I have Boinc 6.2? beta installed with the Applications/Add-Remove tool.

1.  Should I uninstall the 6.2? (beta) using the add/remove tool before doing anything with the 6.4.5 version from getdeb?

2. How do I install the 6.4.5 version I extracted to the new folder in my home directory?

Thanks for your help.

Ken

2.

---

### Post by oldos2er on 2009-01-03
When you first run Boinc manager after installing, click 'Add Project.'

---

### Post by ju2wheels on 2009-01-03
> **california-ken said:**
> Thanks for the reference to the getdeb site.  I downloaded the Boinc client and manager ¨.deb¨ files, placed them into an new folder in my home directory and extracted them and the ¨.gz¨ files they contained into the same folder.

I don know what to do next.  I have Boinc 6.2? beta installed with the Applications/Add-Remove tool.

1.  Should I uninstall the 6.2? (beta) using the add/remove tool before doing anything with the 6.4.5 version from getdeb?

2. How do I install the 6.4.5 version I extracted to the new folder in my home directory?

Thanks for your help.

Ken

2.

1. Yes, remove boinc-manager and boinc-client using the add/remove tool if you have them installed. (You may keep the data directories if it asks.

2. I think you messed up somewhere, you should not have .gz files but rather 2 .deb files from getdeb.net and these should not be extracted using any program. Instead open a command terminal to the directory where you have downloaded these two files and run the following command:

```

sudo dpkg -i *.deb

```

---

