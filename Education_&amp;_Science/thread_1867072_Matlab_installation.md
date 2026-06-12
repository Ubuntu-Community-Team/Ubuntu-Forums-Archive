---
title: "Matlab installation"
date: 2011-10-22
forum: Education &amp; Science
---

### Post by mmsltni on 2011-10-22
Hi everybody.
I have installed matlab but I don't install it in default destination.After that I create Matlab luncher by 
```
sudo wget http://upload.wikimedia.org/wikipedia/commons/2/21/Matlab_Logo.png -O /usr/share/icons/matlab.png
```and

```
sudo wget 'https://help.ubuntu.com/community/MATLAB?action=AttachFile&do=get&target=matlab-r2010b.desktop' -O /usr/share/applications/matlab.desktop
```Now when I lunch it by opening it at usr/share/application It can't run and says :

[HTML]Details: Failed to execute child process "matlab" (No such file or directory[/HTML]What can I do?

And second,Is there any way to install Orcad in linux?Is it possible to install it by virtual box or is there any version of that for Linux?

Thanks.

---

### Post by mmsltni on 2011-10-30
No answer!?Please help mw if you can /...

---

### Post by WasMeHere on 2011-10-30
Hi mmsltni,

There is also ***octave*** that can do quite a lot of the matlab stuff. ```
sudo apt-get install octave
``` Maybe you will be prompted to select one of many versions, e.g. ```
sudo apt-get install octave3.2
```

Have fun finding out :-)
Olle

---

### Post by rewyllys on 2011-10-30
> **mmsltni said:**
> Hi everybody.
I have installed matlab but I don't install it in default destination.After that I create Matlab luncher by 
```
sudo wget http://upload.wikimedia.org/wikipedia/commons/2/21/Matlab_Logo.png -O /usr/share/icons/matlab.png
```and

```
sudo wget 'https://help.ubuntu.com/community/MATLAB?action=AttachFile&do=get&target=matlab-r2010b.desktop' -O /usr/share/applications/matlab.desktop
```Now when I lunch it by opening it at usr/share/application It can't run and says :

[HTML]Details: Failed to execute child process "matlab" (No such file or directory[/HTML]What can I do?

And second,Is there any way to install Orcad in linux?Is it possible to install it by virtual box or is there any version of that for Linux?

Thanks.
Why do you choose to avoid the default destination for Matlab?  You just create problems for yourself by doing so.

---

### Post by 11jmb on 2011-10-30
OrCad is not available to run natively on Linux. You can try it with wine, and it should certainly work on a Windows VM

---

### Post by mikewhatever on 2011-10-30
Since you've picked a non-default location, edit /usr/share/applications/matlab.desktop and provide the path for the matlab executable.

---

### Post by mmsltni on 2011-10-31
> **rewyllys said:**
> Why do you choose to avoid the default destination for Matlab?  You just create problems for yourself by doing so.
I don't have enough space in default dir.
[Olle Wiklund]("http://ubuntuforums.org/member.php?u=571173"),I know octave but I get use to work with matlab...

---

### Post by Blutkoete on 2011-11-05
The simplest solution would be to symlink to the executable (this way you would also be able to launch Matlab from the terminal by typing "matlab").

This requires *sudo* privileges, so be sure to either trust me or check what these commands do before using them. You can do all this without the terminal, but this way it's easier.

```
sudo ln -s <path-to-your-matlab-binary-here> /usr/bin/matlab
```

Then you have to edit the launcher. All launchers are found in the */usr/share/applications/* directory and end in *.desktop*. You need *sudo* privileges to edit things here. Remeber to use *gksudo* instead of *sudo* when invoking graphical applications.

```
gksudo gedit <name-of-the-launcher>
```

In there, you'll find a line that starts with *exec=*. Change whatever is behind that to *matlab -desktop*. With the *-desktop* option, Matlab doesn't require an open and unusable terminal all the time.

Good luck!

P.S.: Step 2 will only work if you did step 1 as well.

---

### Post by Sightes on 2011-11-12
thanks for the code :)

---

