---
title: "Directory change problem in Shell Script"
date: 2009-06-02
forum: General Help
---

### Post by lockhid on 2009-06-02
Hi,
I'm facing problem scripting shell script. I'm currently using 
Ubuntu 9.04 (Jaunty). I've no modem driver, so I downloaded 'vlc' player
and its related pkgs from 'packages.ubuntu.com'. I wanted to create a 
shell script which would install all the pkgs serially 
(pkgs [depends] would be followed). 
my pkgs directory structure is given below

```
/root/ubuntu-pkgs
|-->pkgs
|   |-->hardy
|   |-->jaunty
|
|-->vlc-plugin
|   |-->hardy
|
|-->vlc
|   |-->hardy
```

So, I created the following script. Script name is 'vlc-install_i386.sh' 
and it is in the "/root/ubuntu-pkgs/vlc/hardy" directory.

script:
---------------------------------
```
cd ../../vlc/hardy
dpkg --install <package-name.deb>

cd ../../pkgs/hardy
dpkg --install <package-name.deb>
dpkg --install <package-name.deb>
.........
dpkg --install <package-name.deb>

cd ../../vlc/hardy
dpkg --install vlc-nox_*.deb

cd ../../vlc-plugin/hardy
dpkg --install <package-name.deb>
....
dpkg --install <package-name.deb>

cd ../../vlc/hardy
dpkg --install vlc_*.deb
```

---------------------------------
I access to that directory 'vlc' and run the script from terminal
by the './vlc-install_i386.sh' (without ') command.
but, it's not working except the pkgs from 'vlc/hardy' directory 
(the script is run from this dir). Console shows ' No such Archive'
and pkgs are not installed. I think 'cd' is not changing the dir.

How this will work? Please help me.

Sincerely,
Lockhid

---

### Post by dcstar on 2009-06-02
> **lockhid said:**
> Hi,
I'm facing problem scripting shell script. I'm currently using 
Ubuntu 9.04 (Jaunty). I've no modem driver, so I downloaded 'vlc' player
and its related pkgs from 'packages.ubuntu.com'. I wanted to create a 
shell script which would install all the pkgs serially 
(pkgs [depends] would be followed). 
my pkgs directory structure is given below
.........
How this will work? Please help me.

Sincerely,
Lockhid

**You** do not decide where .deb packages put their files, so it is totally irrelevant as to where the install process is run - just install them in whatever order **they** need to be installed.

---

### Post by lockhid on 2009-06-03
dcstar,
Thanks for your reply. But, I think you don't get this right. My software pkgs are in different folders. I want to make an automated process for every software I have (vlc, wine, wvdial, gnome-ppp etc). I don't want to install all the necessary pkgs needed for soft manually by traversing all these folders. An installer script will help to install a soft easily. The script I showed easily works on Windows (of course, proper syntax, but the theme is same). But it is not working on linux specially 'cd' command. Whether I write pkgs-name with it's directory (dpkg -i /root/pkgs/<pkgs-name>.deb) or I first change the directory, dpkg always mentioned that pkgs are missing.

I think I cleared my theme. I really need the proper suggestion.

Sincerely,
Lockhid

---

### Post by lockhid on 2009-06-03
-

---

### Post by Tibuda on 2009-06-03
Have you tried
```
cd /root/ubuntu-pkgs
dpkg --install **/`lsb_release -cs`/*.deb
``` ?

---

### Post by michy99 on 2009-06-03
Have you tried using an absolute directory instead of a relative directory for the first cd command? That way you are sure it is starting out in the right place.

```
cd /root/ubuntu-pkgs/vlc/hardy
```

---

### Post by lockhid on 2009-06-03
Hi michy99,

I've tried. It's not working. I'm uploading script and terminal output files in the following link-

[http://cid-46bf0b8e49df04c4.skydrive.live.com/self.aspx/.Public/vlc-files.zip]("http://cid-46bf0b8e49df04c4.skydrive.live.com/self.aspx/.Public/vlc-files.zip")

I will be glad if anyone check it.

---

### Post by michy99 on 2009-06-03
Ok, everything is going fine until it hits```
cd ../../pkgs/jaunty
```The first thing that comes to mind is that you may have mis-spelled the directory name. Please double-check the spelling of the actual directory.

---

### Post by lockhid on 2009-06-04
Hi, michy99

The directory structure is ok. I even check the command you marked in Windows command prompt -

```
E:\ubuntu-pkgs\pkgs\hardy>cd ../../pkgs/jaunty

E:\ubuntu-pkgs\pkgs\jaunty>
```

---

### Post by lockhid on 2009-06-04
Hi,

I've captured my 'ubuntu-pkgs' directory tree from Windows. It is given below

[http://cid-46bf0b8e49df04c4.skydrive.live.com/self.aspx/.Public/dir-struct.png]("http://cid-46bf0b8e49df04c4.skydrive.live.com/self.aspx/.Public/dir-struct.png")

The directory structure is ok.

---

### Post by lockhid on 2009-06-04
I have edited the script and set 'pwd' and some border for marking. All the directory changing in the script are using relative path. So, when I execute the script using 

```
./vlc-install_i386.sh
```

(I also tried with the following)
```
sh vlc-install_i386.sh
```

it is executed fine but when it reaches to almost last point it shows directory missing (No such file or directory) several times and in the last it is executed fine. So, the point it shows error I change the directory path relative to absolute and executed the script again. But the answer is same. I have captured my directory structure, terminal output and the script in the following zip file-

[http://cid-46bf0b8e49df04c4.skydrive.live.com/self.aspx/.Public/vlc-op.zip]("http://cid-46bf0b8e49df04c4.skydrive.live.com/self.aspx/.Public/vlc-op.zip")

The directory structure is ok. I even check the command in the terminal which is not working in the script -

```
cd ../../pkgs/jaunty
```

it is working but not in the script. I think it is a bug.

Can anyone help with this? I'd really appreciate if anyone help me.

---

### Post by lockhid on 2009-06-10
**===================================================**
**SOLVED!!!!!!!!!!!!!!!!!SOLVED!!!!!!!!!!!!!!!!SOLVED**
**===================================================**
The problem is solved. Actually it's caused because I edited some parts
of this script in Windows and Windows use line terminator 'CRLF' pair and
Unix family os use only 'LF'. The problem caused by 'CR' - carrige return code.

You can see the solution thread from the following link-

[http://ubuntuforums.org/showthread.php?t=1183334]("http://ubuntuforums.org/showthread.php?t=1183334")

thanks, **asmoore82** for giving an excellent solution with a demonstration.

---

