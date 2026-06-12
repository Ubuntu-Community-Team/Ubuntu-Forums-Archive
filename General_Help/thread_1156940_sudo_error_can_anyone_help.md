---
title: "sudo error? can anyone help?"
date: 2009-05-12
forum: General Help
---

### Post by Ichindar on 2009-05-12
hi, im fairly new to ubuntu, i tried to fix amarok today, but now i keep getting a big red circle on my task bar and the following messages when i go to the "update manager"


Could not initialize the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'sudo' is not known on line 3 in source list /etc/apt/sources.list.d/amarok.list, E:The list of sources could not be read.'

and i get this from the synaptic package manager

E: Type 'sudo' is not known on line 3 in source list /etc/apt/sources.list.d/amarok.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

can anyone help me? cheers

---

### Post by kpkeerthi on 2009-05-12
Post the output of ```
cat /etc/apt/sources.list.d/amarok.list
```

---

### Post by mktoni on 2009-05-12
It seems to be an issue with your sources list for amarok.
Check the file /etc/apt/sources.list.d/amarok.list
Look for a malformed line. One with "sudo" in it.
Post it here.

---

### Post by Ichindar on 2009-05-12
i got this

-laptop:~$ cat /etc/apt/sources.list.d/amarok.list
deb [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \
0x1d7e9dd033e89ba781e32a24b9f1c432ae74ae63

---

### Post by mktoni on 2009-05-12
Edit amarok.list file, comment the line starting with sudo, save the file and try again.

Like this:
#sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \
0x1d7e9dd033e89ba781e32a24b9f1c432ae74ae63

---

### Post by Ichindar on 2009-05-12
sorry, im very new to all this code business, i dont understand what you mean or what i should do?

---

### Post by kpkeerthi on 2009-05-12
1. Open the file: ```
gksudo gedit /etc/apt/sources.list.d/amarok.list
```
2. Delete the below lines
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \
0x1d7e9dd033e89ba781e32a24b9f1c432ae74ae63
```
3. Save and Exit
4. Now run this command at the terminal prompt:```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0x1d7e9dd033e89ba781e32a24b9f1c432ae74ae63
```
5. ```
sudo apt-get update
```

---

### Post by mktoni on 2009-05-12
You must to edit the file /etc/apt/sources.list.d/amarok.list 

# sudo editor /etc/apt/sources.list.d/amarok.list

Add a # at beginning of the line 
 
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \
0x1d7e9dd033e89ba781e32a24b9f1c432ae74ae63 	

Like this:

#sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \
 0x1d7e9dd033e89ba781e32a24b9f1c432ae74ae63 	

Save the file and it should work.

---

### Post by Ichindar on 2009-05-12
sorry, i dont understand what to do with all that stuff you wrote? i need it in idiot terms haha, i dont know where to go or where to put that code etc?

---

### Post by Ichindar on 2009-05-12
awesome, that worked, thanks so much :)

i dont suppose you know a good place to look to learn terminal commands etc do you?

---

### Post by kpkeerthi on 2009-05-12
> **Ichindar said:**
> awesome, that worked, thanks so much :)

i dont suppose you know a good place to look to learn terminal commands etc do you?

Check out the links in my signature.

---

