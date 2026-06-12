---
title: "Installing new Packages"
date: 2009-01-07
forum: General Help
---

### Post by arepaking on 2009-01-07
Hello experts,
I recently installed Adobe Reader from a .deb file. My understanding is that apps within Ubuntu will remain up-to-date as long as you can see them in SPM (Synaptic). After the installation process finish, I am able to see the Adobe icon in Applications->Office; so far so good.

Now, I went to SPM, on the left side options, I clicked "ALL" and I tried to search for "adobereader-enu" to see if the package will be there, for my surprise there is nothing called "adobereader-enu".

Does this mean that my Adobe reader installation was not right? 

As a side note, if I click on Installed (Local or obsolete) I see the package "adobereader-enu". I just want to make sure that my Adobe Reader is properly installed and it will be check for new updates as they are being released.

Thanks in advance for your support.
AK

---

### Post by danwood76 on 2009-01-07
If you install a .deb file that is not in the ubuntu repositories it wont be updated with system updates as it is not maintained bu the ubuntu community.
You need to add a repository for stuff like that to happen.

It should display the installed file in synaptic, try just searching adobe.

---

### Post by Irony on 2009-01-07
If you installed the deb file from outside the repositories then it will appear in local or obsolete and also appear in all.

Local refers to you installing it from outside the repositories - in this case you just clicked on the deb and gdebi (or dpkg) installed it.

---

### Post by arepaking on 2009-01-10
Thanks guys for your reply.

But, do you know if it is possible to add the adobe reader to the Third-party software sources? This way it will be up-to-date within time correct?

Regards,
AK

---

### Post by todak on 2009-01-10
Installing it from the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository will ensure it is updated automatically through update manager. Anything installed from outside a repository must be updated manually.

---

### Post by binbash on 2009-01-10
> **arepaking said:**
> Thanks guys for your reply.

But, do you know if it is possible to add the adobe reader to the Third-party software sources? This way it will be up-to-date within time correct?

Regards,
AK

you can install it from medibuntu repos

---

### Post by stanca on 2009-01-10
If you installed it already it should appear in menu>office.
You can install ultamatix and from there you can install adobe reader and many other usefull apps.:wink:
[http://ultamatix.com/#download](http://ultamatix.com/#download) .

---

### Post by arepaking on 2009-01-10
> **todak said:**
> Installing it from the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository will ensure it is updated automatically through update manager. Anything installed from outside a repository must be updated manually.

Ok, I decided to uninstall the application (since I installed the program by executing the .deb file). Then I added the Medibuntu repository and the adobe reader is being download as I writing this post.

One more thing, I couldn't add the GPG key. According to the website you just need to execute this code: 
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

But when I did that I got the following error message:
```
Fetched 199B in 1s (109B/s)
W: GPG error: http://packages.medibuntu.org intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

Am I doing something wrong here?

Thanks guys!

---

### Post by todak on 2009-01-10
> **arepaking said:**
> 
One more thing, I couldn't add the GPG key. According to the website you just need to execute this code: 
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

But when I did that I got the following error message:
```
Fetched 199B in 1s (109B/s)
W: GPG error: http://packages.medibuntu.org intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

Am I doing something wrong here?

Thanks guys!

You may have discovered by now that you can only run one process of a package manager at a time. For instance, your error message was generated due to the fact that you probably still had Synaptic open while you were trying to apt-get in a terminal.

---

### Post by arepaking on 2009-01-11
> **todak said:**
> You may have discovered by now that you can only run one process of a package manager at a time. For instance, your error message was generated due to the fact that you probably still had Synaptic open while you were trying to apt-get in a terminal.

You are absolutely right! I will never forget this!. Thank you very much for your help and patience.

Kind Regards,
AK

---

