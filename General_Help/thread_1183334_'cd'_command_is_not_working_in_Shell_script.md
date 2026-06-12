---
title: "'cd' command is not working in Shell script"
date: 2009-06-10
forum: General Help
---

### Post by lockhid on 2009-06-10
Hi
I'm facing a problem scripting shell script. I have Ubuntu 9.04 (Jaunty) currently installed. I've downloaded some software packages from "packages.ubuntu.com" site. I wanted to create some script for those pkgs to install those softwares. My softs are in different folders. I've created a script to install 'vlc' player. I executed it from '/root/ubuntu-pkgs/vlc/hardy' folder. I've used relative path in 'cd' command. When I execute it using the following commands

```
./vlc-install_i386.sh
```

or
```
sh vlc-install_i386.sh
```

the script is failed in the middle. So, I have edited the script and set 'pwd' and some border for marking. I tried again, it is executed fine but when it reaches to almost last point it shows directory missing (No such file or directory) several times and in the last it is executed fine. So, the point it shows error I change the directory path relative to absolute and executed the script again. But the answer is same. I have captured my directory structure, terminal output and the script in the following zip file-

[http://cid-46bf0b8e49df04c4.skydrive.live.com/self.aspx/.Public/vlc-op.zip]("http://cid-46bf0b8e49df04c4.skydrive.live.com/self.aspx/.Public/vlc-op.zip")

The directory structure is ok. I even check the command in the terminal (and off course in Windows) which is not working in the script -

```
cd ../../pkgs/jaunty
```

it is working but not in the script. I think it is a bug.

Can anyone help with this? I'd really appreciate if anyone help me.

---

### Post by asmoore82 on 2009-06-10
you should never use relative paths ``../'' in a shell script
unless your script `cd`s itself somewhere first -
even then it's probably not a very good idea.

the initial working directory of a script is not where the script resides -
it is where the user was in they invoked the script -
in other words, it could be absolutely anywhere.

by starting off with `cd ../../...` you are making assumptions about the file layout anyway -
so go ahead and make the assumptions bold and absolute and make the script fail if the assumption is wrong -
also make the script fail if `cd`ing is not successful for any reason...
```
pwd="/root/ubuntu-pkgs/pkgs"
if [ ! -d "$pwd" ]; then
   echo "ERROR: ${pwd}: no such directory. ABORT" 1>&2
   exit 1
fi

cd "$pwd" || exit 127
...
```

next thing, go ahead and make your script a real BASH script:
make this the absolute first line: ```
#!/bin/bash
```
make it executable: ```
chmod +x *"my_script.sh"*
```
now you can invoke it directly.

parts of your script have been poisoned by a so called "text" editor that
uses CRLF line terminators - most likely from a windoze system.
the full version of the `vim` editor can clean this up:
```
**bash ~$** file vlc-install_i386.sh
vlc-install_i386.sh: ASCII text, with CRLF, LF line terminators
**bash ~$** vi vlc-install_i386.sh
[COLOR="Red"]**vim$**[/COLOR][COLOR="Blue"] :%s:\r:\r:g[/COLOR]
**bash ~$** file vlc-install_i386.sh
vlc-install_i386.sh: ASCII text
```
You would need to type [COLOR="Blue"]*these*[/COLOR] keystrokes exactly in vim.

---

### Post by asmoore82 on 2009-06-10
I've tested and I'm fairly sure the poisoned text is the cause of the original problem:

I have a command listing for testing named "test" ...
```
**asmoore@ubuntu-lenovo:~$** cat -A test
cd Pictures$
pwd$
**asmoore@ubuntu-lenovo:~$** bash test
/home/asmoore/Pictures
**asmoore@ubuntu-lenovo:~$** file test
test: ASCII text
**asmoore@ubuntu-lenovo:~$** vi test #manually add CRLF "DOS" newline
**asmoore@ubuntu-lenovo:~$** cat -A test
cd Pictures**[COLOR="Red"]^M[/COLOR]**$
pwd$
**asmoore@ubuntu-lenovo:~$** file test
test: ASCII text, with CRLF, LF line terminators
**asmoore@ubuntu-lenovo:~$** bash test
: No such file or directory
/home/asmoore
```

---

### Post by lockhid on 2009-06-10
**SOLUTION ACKNOWLEDGEMENT**

Thanks **asmoore82**, for giving an excellent solution with a demonstration. 

You were right about the problem. I examined the script with my own 'UniCode Editor' tool Windows and found the 'CRLF' combinations.  I've removed the 'CR' codes and it's working fine.

Actually, When I used Ubuntu 8.04 LTS (Hardy), I installed all these packages manually because the script wasn't working at all. I used "apt-get install <package-name>" instead of using "dpkg --install <filename_*.deb> in script and that's why it was not working. I installed (manually) 'vlc' properly with no dependency problem. 

So, when I installed Ubuntu 9.04 (Jaunty), I corrected the script and it installed all the packages but with one dependency problem. A package named "libcucul0_0.99.beta16-1_all.deb" was missing (It didn't show in earlier version of Ubuntu). So, I downloaded the package from Windows XP and edited the script in the same OS and put the package near the end of the script (also modified some package below that, about 4/5). So, from that point the problem started, because of editing in Windows.

---

### Post by lisati on 2009-06-10
Attached is the source for a short cross-platform program in "C" that might be of help for other people in similar situations, where a file has been "poisened" by "wrong" line breaks. 

I've tested it with GCC on 64-bit Jaunty and Turbo C++ v3 under Win 98SE. It won't compile with Turbo C 2.01 (wrong comment style for one thing)

Usage: ```
[./]fixlf <inputfilename> <outputfilename>
```

Feel free to use and modify it as you see fit. (In its current form it works best with Linux and MS-DOS/Windows line breaks. It's likely to need modifications if you have a file with "MAC"-style linebreaks that you want to convert.)

---

### Post by slakkie on 2009-06-10
I use this script:

```

#!/bin/bash

DOSFILE="$1"
UNIXFILE="${DOSFILE}.unix"

if [ ! -e "$DOSFILE" ] ; then
  printf "Usage: %s [file to convert]\n" `basename $0`
  exit 2
fi

cp "$DOSFILE" "$DOSFILE.dos"
tr -d '\r' < "$DOSFILE" > "$UNIXFILE"
mv "$UNIXFILE" "$DOSFILE"

```

---

### Post by nitinbobade on 2009-07-06
:guitar:> **asmoore82 said:**
> you should never use relative paths ``../'' in a shell script
unless your script `cd`s itself somewhere first -
even then it's probably not a very good idea.:guitar:
 
the initial working directory of a script is not where the script resides -
it is where the user was in they invoked the script -
in other words, it could be absolutely anywhere.:guitar:
 
by starting off with `cd ../../...` you are making assumptions about the file layout anyway -
so go ahead and make the assumptions bold and absolute and make the script fail if the assumption is wrong -
also make the script fail if `cd`ing is not successful for any reason...
```
pwd="/root/ubuntu-pkgs/pkgs"
if [ ! -d "$pwd" ]; then
   echo "ERROR: ${pwd}: no such directory. ABORT" 1>&2
   exit 1
fi
 
cd "$pwd" || exit 127
...
```
 
next thing, go ahead and make your script a real BASH script:
make this the absolute first line: ```
#!/bin/bash
```
make it executable: ```
chmod +x *"my_script.sh"*
```
now you can invoke it directly.
 
parts of your script have been poisoned by a so called "text" editor that
uses CRLF line terminators - most likely from a windoze system.
the full version of the `vim` editor can clean this up:
```
**bash ~$** file vlc-install_i386.sh
vlc-install_i386.sh: ASCII text, with CRLF, LF line terminators
**bash ~$** vi vlc-install_i386.sh
[COLOR=red]**vim$**[/COLOR][COLOR=blue] :%s:\r:\r:g[/COLOR]
**bash ~$** file vlc-install_i386.sh
vlc-install_i386.sh: ASCII text
```
You would need to type [COLOR=blue]*these*[/COLOR] keystrokes exactly in vim.

---

### Post by loomsen on 2009-07-06
pushd and popd actually are thought to provide a proper solution, or am i wrong?

---

### Post by OlJack on 2010-01-14
I had major problems getting cd to work in scripts too. After days of work, and some help from this thread that put me over the top, I found the following scripting rules for me, and hope they might help others. using Ubuntu 9.04, I found:
 
1. Remove windows-hangover characters (that show up in emacs as ^M and are Linefeed/Carrage-return hangovers from windows editing). Use a clean editor like emacs or vim. Note: gedit will edit those files and not add the bad characters, but it will leave them there and not remove them, OR display them. [learned this from this present thread, above.]
 
2. Do NOT put sudo -s in the script.
 
3. Do NOT put a "sudo" prefix on the "cd" command.
 
4. When using nautilus to launch the script (double-click on the script), answer 
"Run in Terminal" and NOT "run" to the query about what to do with the command. Note: it does not have to be in nautilus's script directory to be invoked if the other rules, above, are followed.
 
As a general observation, there is a feeling that composing scripts is very sensitive. Shell Scripts are fragile; they are not robust. Tiny little infractions cause them to fail with zero messages as to what, why, where, or whatever.

---

