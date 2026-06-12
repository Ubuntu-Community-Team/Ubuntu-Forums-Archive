---
title: "Skype"
date: 2008-12-31
forum: General Help
---

### Post by Narendran257 on 2008-12-31
I am trying to install skype.
Have any of you done it? Please explain.
I have installed the 20 packages of Skype Debian 2.0.0
how do I proceed. I do not have a Skype logo on the screen and am not able to get the Skype screen.

---

### Post by adult swim on 2008-12-31
edit: woops i didnt realize skype was in medibuntu repository.  follow ajmorris advice.

---

### Post by ajmorris on 2008-12-31
hi there,
you can use apt to install skype in ubuntu via the *mediubuntu* repositories.

Just run the following commands to get skype installed:
```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

that will add the mediubuntu repos to your sources.list, and run an apt-get update so that your repositories are up to date, and the mediubuntu repositories are also in them.

Then just run this to install skype:
```

sudo aptitude install skype
```

then you can run skype from either the CLI, or from your menus.
Enjoy,


AJ

---

### Post by SonnHalter on 2008-12-31
or you can just go install ultamatix and it will autoinstall it for you.

---

### Post by jespdj on 2008-12-31
> **SonnHalter said:**
> or you can just go install ultamatix and it will autoinstall it for you.
Note that ultamatix is a dangerous tool that can screw up your system. Just install it via the Medibuntu repository, that's the easiest and safest way to install Skype (and Google Earth and other software).

---

### Post by ajmorris on 2009-01-01
> **SonnHalter said:**
> or you can just go install ultamatix and it will autoinstall it for you.

hi there,
please avoid suggesting the use of third party package managers, they are not officially supported by the Ubuntu Forums. Especially when they have tendencies to cause weird behaviour in OSs. Ultimatix is basically the replacement AutomatiX. It is going to go the same way as it ;)

AJ

---

### Post by jespdj on 2009-01-01
-

---

### Post by inearlygaveup on 2009-03-26
> **ajmorris said:**
> hi there,
you can use apt to install skype in ubuntu via the *mediubuntu* repositories.

Just run the following commands to get skype installed:
```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

that will add the mediubuntu repos to your sources.list, and run an apt-get update so that your repositories are up to date, and the mediubuntu repositories are also in them.

Then just run this to install skype:
```

sudo aptitude install skype
```

then you can run skype from either the CLI, or from your menus.
Enjoy,


AJ

Can anyone help – I want to install Skype using the above commands but am unsure about how to use them.
1	I assume I type them into the Terminal
2	Is the first set of codes – separate commands do I hit   enter after entering each line
3	Can I cut and paste the commands.

---

### Post by LowSky on 2009-03-26
Dont use the above command they are form an older release, and wont work

use these instructions
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

1. yes terminal
2. seperate lines do one line at a time
3. yes, best thing to do use the mouse right click feature or if using the keyboard, when pasting into terminal you need to use Ctrl+Shift+V for pasting, to copy from the terminal use Ctrl+Shift+C... some people dont know this little quirk about pasting in terminal

---

### Post by inearlygaveup on 2009-03-26
Thanks for the update and help - I also didn't know about the Ctrl+Shift+C and V (I used the Ctrl C & V a lot in windows. 

Out of interest how do you get the straight up & down character as shown on the original post > -O- | sudo apt-key

---

