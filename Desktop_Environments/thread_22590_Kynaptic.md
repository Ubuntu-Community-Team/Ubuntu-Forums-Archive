---
title: "Kynaptic"
date: 2005-03-28
forum: Desktop Environments
---

### Post by Leebobs on 2005-03-28
How do I add repositaries to Kynaptic?

---

### Post by techlord on 2005-03-28
you have to manually edit the /etc/apt/sources.list file

---

### Post by apokryphos on 2005-03-28
You might also consider trying out KPackage.

---

### Post by Stephen-I-M on 2005-03-28
Thanks for mentioning kpackage -- I like it better already than kynaptic. Any way to make the font a bit smaller? It really has a lot of info to display.

Stephen

---

### Post by bailout on 2005-03-28
[QUOTE=apokryphos]You might also consider trying out KPackage.[/QUOTE]

Is kpackage fully compliant with the ubuntu update system. If so I wonder why kubuntu are developing kynaptic?

---

### Post by apokryphos on 2005-03-29
I agree that KPackage is better, and I think it would serve a great default. The issue has been raised on the kubuntu-devel mailing-list: [http://lists.ubuntu.com/archives/kubuntu-devel/2005-March/000168.html](http://lists.ubuntu.com/archives/kubuntu-devel/2005-March/000168.html) If any of you have preference, then please drop a note to the mailing list, or let the devs know why you think one is better in #kubuntu-devel IRC Channel.

Stephen-I-M, the fonts work very well here, and the program -- like the majority of KDE programs -- just takes the font from the settings in kcontrol. Are you perhaps running the program as root? Or, even sudo? KPackage doesn't need to be run thusly, because it doesn't use apt until you want to commit the changes; hence, the root password is only required when commiting the changes.

---

### Post by KDE-fan on 2005-03-29
I think it is silly that every Linux-distribution has it own package-manager: Mandrake with MCC, SuSE with YAST etc. etc. Spending resources on developing Kynapse would be a great mistake if KPackage already works perfectly with Kubuntu. I'll check it out later today.

---

### Post by Stephen-I-M on 2005-03-29
[QUOTE=apokryphos]
Stephen-I-M, the fonts work very well here, and the program -- like the majority of KDE programs -- just takes the font from the settings in kcontrol. Are you perhaps running the program as root? Or, even sudo? KPackage doesn't need to be run thusly, because it doesn't use apt until you want to commit the changes; hence, the root password is only required when commiting the changes.[/QUOTE]

I'm having a problem running it as a user. I get this when asked for the root password:

  Password: 
  su: Authentication failure
  Sorry.

I'm sure the password is correct. I wonder if this is because ubuntu doesn't use su?

Stephen

---

### Post by odrop on 2005-03-30
Did you try running the program (or whatever you are doing) with sudo?  Remember, Kubuntu and Ubuntu use sudo instead of using a root account and using su.  Search around the forums or on the wiki for a lot of information about it and why.

---

### Post by Stephen-I-M on 2005-03-30
[QUOTE=odrop]Did you try running the program (or whatever you are doing) with sudo?  Remember, Kubuntu and Ubuntu use sudo instead of using a root account and using su.  Search around the forums or on the wiki for a lot of information about it and why.[/QUOTE]
Normally I do, but see the post I quoted above, where it says that kpackage doesn't need to be run with sudo.

By the way, can I set up a kmenu that runs kpackage with sudo?

Stephen

---

### Post by apokryphos on 2005-03-30
Stephen-I-M, the KPackage package hasn't yet been tweaked to especially use sudo, unfortunately. Running it with kdesu might work, but otherwise you'll have to use the actual *root* password when it requests it (not yours). See the wiki on setting this up; basically, all you need is "sudo passwd". 

Hopefully they'll look into it in the near future.

---

### Post by JeffreyCentex on 2005-03-30
You can use kdesu with kpackage (by editing the menu) if you have a recent kde install.  If it doesn't work, try updating...

---

