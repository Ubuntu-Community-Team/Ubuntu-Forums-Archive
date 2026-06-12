---
title: "Can't install Quake 3 demo"
date: 2006-11-27
forum: Gaming &amp; Leisure
---

### Post by theosib on 2006-11-27
I'm running Dapper, and I'd like to install the Quake III demo.

When I run the script that I downloaded (linuxq3ademo-1.11-6.x86.gz.sh), it pops up a window too quickly for me to read it (I catch something about "not found"), and then does nothing.  No error messages are given to me (naturally--who needs error messages when things go wrong).

Does anyone have any suggestions on how to install this?

Thanks.

---

### Post by theosib on 2006-11-27
I've managed to make some headway into why it isn't working.  I launch the script (which starts an xterm), and then quickly switch to the terminal I launched it from and hit ctrl-z.

The last few errors I see look like this:

Error: no such file "-r"
Error: no such file "-n"
Error: no such file "Verifying"
Error: no such file "archive"
Error: no such file "integrity..."

I've tracked that down to this block of code in the script:

echo=echo; [ -x /usr/ucb/echo ] && echo=/usr/ucb/echo
if type print > /dev/null 2>&1; then echo="print -r "; fi
mkdir $tmpdir || {
        $echo 'Cannot create target directory' $tmpdir >&2
        $echo 'you should perhaps try option -target OtherDirectory' >&2
                eval $finish; exit 1;
}
$echo -n Verifying archive integrity...

So, it defines a new echo, and when it tries to use it, it doesn't work as expected.

What the heck is going on here?

---

### Post by aidanr on 2006-11-27
[http://ubuntuforums.org/showthread.php?t=258823](http://ubuntuforums.org/showthread.php?t=258823)

---

### Post by Xyhthyx on 2006-11-28
First chmod +x it (or right-click->properties->allow to run as program)
```
chmod +x linuxq3ademo-1.11-6.x86.gz.sh
```

Then do this to extract it
```
sh linuxq3ademo-1.11-6.x86.gz.sh -target ~/q3
```

Chmod 755 that q3 folder folder
```
sudo chmod 755 ~/q3
```

Use Nautilus and go to ~/q3/bin/x83/glibc-2.0/ and copy or move the files libMesaVoodooGL.so and q3demo to your ~/q3 folder.

Now make a symbolic link of libGL.so to your q3 folder
```
ln -s /usr/lib/libGL.so.1 ~/q3/libGL.so
```

Now cd to your q3 folder and do ./q3demo

---

### Post by dmn_clown on 2006-11-28
The chmod is a pointless step,

```
sh linuxq3ademo-1.11-6.x86.gz.sh -target ~/q3
```

will work just fine without the script being executable.

---

### Post by theosib on 2006-11-28
Unfortunately, the suggestion given in that other post doesn't work.  It keeps complaining about there being no file named "-r".  Apparently, the script is calling some program called "print" indirectly via a variable $echo, and that print doesn't accept -r as an option.

---

### Post by castano on 2009-01-03
This worked for me:

[http://ubuntuforums.org/showpost.php?p=6484626&postcount=8](http://ubuntuforums.org/showpost.php?p=6484626&postcount=8)

---

