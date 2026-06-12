---
title: "Noob question, should be easy for gurus..."
date: 2005-05-05
forum: Desktop Environments
---

### Post by Joey French on 2005-05-05
How can I revert back to the default repositories list that came with Kubuntu/ Ubuntu? Somehow along the way I messed them up, and now I get all types of "could not stat:" errors. I have been trying to add universe/ multiverse, but I think I changed my sources/ binaries, and I am new, and have searched high and low, please help... ](*,)

---

### Post by Xerampelinae on 2005-05-05
Perhaps follow this little guide.  Except when it says to find a certain section and replace it with another, just paste the replacement as the only thing in the file /etc/apt/sources.list

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

It's not the default that came with Ubuntu, but it's probably better.

---

### Post by bored2k on 2005-05-05
[QUOTE=Xerampelinae]Perhaps follow this little guide.  Except when it says to find a certain section and replace it with another, just paste the replacement as the only thing in the file /etc/apt/sources.list

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

It's not the default that came with Ubuntu, but it's probably better.[/QUOTE]
 I wouldn't recommend those because they have MARILLAT inside. That will give a myriad of dependency problems in the not distant future.. It's good though

---

### Post by Joey French on 2005-05-05
Okay, so I pasted them in,still problems came back:

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-amd64_Packages) - stat (2 No such file or directory)

Any ideas? Help...Again I am new!

---

### Post by Joey French on 2005-05-07
Come on, this should be really easy...

---

### Post by XDevHald on 2005-05-07
[QUOTE=Joey French]Come on, this should be really easy...[/QUOTE]
 Let's make this easy guys...

 >  ## UBUNTU MAIN
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## UBUNTU UNIVERSE
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

## UBUNTU SECURITY
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## UBUNTU MULTIVERSE
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted 

The two very bottom backports of deb are from the 3rd Party Projects backend.

Link ---> [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)   Please note that if you want to get the new gaim, firefox, gimp, and other repositories from UbuntuForums Backports then add the following lines located in the quote above at the bottom as well along with the rest of them.

---

### Post by Psquared on 2005-05-07
Dude, do this:

Open a terminal
Type: sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
Type: sudo gedit /etc/apt/sources.list
Delete the contents by highlighting (select everything) and click delete
Copy the text from the sources.list post above into the gedit window (I hate that word) that should be blank right now
Make sure you got everything word for word
Click save
Exit gedit and close terminal by typing "exit"
Open synaptic
Click "reload"

If you get errors at this point it is probably because (a) the servers are down or (b) your internet connection is down or blocked.

Try again later if it does not work

That should do it.

---

### Post by Joey French on 2005-05-07
Thankys, guys. I know these things can be pretty annoying for experts, but for the newb with a serious desire to understand the Linux / Ubuntu OS, help like this can mean a lot. Much appreciated.

---

### Post by Psquared on 2005-05-07
No problem.

---

