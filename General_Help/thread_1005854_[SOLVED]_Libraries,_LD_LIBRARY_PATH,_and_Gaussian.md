---
title: "[SOLVED] Libraries, LD_LIBRARY_PATH, and Gaussian"
date: 2008-12-08
forum: General Help
---

### Post by knowname on 2008-12-08
I've just installed some scientific software (Gaussian) that sets the variable LD_LIBRARY_PATH as part of my .bashrc script. I've read that this is sloppy programming, and I've determined that when I allow the software to set this variable, I start getting problems. Specifically, if I run "gedit" from the prompt, I get:

```
gedit: symbol lookup error: /usr/lib/libcairo.so.2: undefined symbol: FT_Library_SetLcdFilter
```

and gedit immediately crashes/closes. Unfortunately, if I comment out the lines in .bashrc that modifiy LD_LIBRARY_PATH, the new software (Gaussian) will not run.

Gaussian (actually g03 and gv/gview) was distributed to me already compiled, so I can't recompile.

Any suggestions on how I can get Gaussian to look in these special library directories, but have every other program still retain the original behavior with respect to libraries? I'm running Ubuntu 8.04.

Thanks!

---

### Post by snova on 2008-12-08
Prefix the command with the new environment variable, like so:

[PHP]LD_LIBRARY_PATH="/new/value" g03[/PHP]

The new value should not propogate beyond this one command.

I suggest you create an alias or function for this, or a short script.

---

### Post by knowname on 2008-12-08
That worked. Thanks so much!

---

### Post by knowname on 2008-12-08
For the record, in case anyone else is trying this, here's what I did. I put these commands in my ~/.bashrc so they automatically load when I log in to ubuntu. For GaussView (gv), I added the command

```
gv () { LD_LIBRARY_PATH=$g03root"/gv/lib" $g03root/gv/gview; }
```

(where g03root="/usr/chem", in my case). For Gaussian (g03), it was slightly more complicated for two reasons (1) I need to pass it an argument, and (2) I can't keep the command 'g03', since the directory g03 is in is executable (in the PATH variable), and it needs to stay that way since g03 calls many other executables from its own directory. Therefore, I used the following code and named the function g3:

```
g3 () 
{
gr=$g03root
GAUSS_EXEDIR="$gr/g03/bsd:$gr/g03/private:$gr/g03"
LD_LIBRARY_PATH=$GAUSS_EXEDIR
g03 $1
}
```

where $1 is the argument passed to g3, e.g., 'g3 glucose.gjf'.

There are more steps than this to getting gaussian running on ubuntu, but these are the only ones relevant to LD_LIBRARY_PATH. If someone runs runs into other problems in installing this program, feel free to ping me.

---

### Post by susruta101 on 2008-12-17
I am using Ubuntu 8.04. For me Gaussian is running fine without any issues but I have problem with gaussview. Whenever I try to run it, it shows...

> /home/smgr/bin/gv/gview: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

I added the following script in my ~/.bashrc file
```
export GV_DIR='/home/smgr/bin/gv'
alias gv03=$GV_DIR'/gview'
alias gview=$GV_DIR'/gview'
if [ "$LD_LIBRARY_PATH" ]
then
   export LD_LIBRARY_PATH=$GV_DIR'/lib:'$LD_LIBRARY_PATH
else
   export LD_LIBRARY_PATH=$GV_DIR/lib
fi

```

What should I do? The posint to be noted is... there is no prob with my libstdc etc package. I am sure that they are in their updated state.
Thanks in advance.
Susruta

---

### Post by knowname on 2008-12-17
If my notes are correct, I ran into this problem as well and I believe I needed to add "libstdc++2.10-glibc2.2_2.95.4-24_i386.deb". However, this appears to not exist in the Hardy repositories, so I had to grab a copy from the gutsy repositories:

[http://packages.ubuntu.com/gutsy/libstdc%2B%2B2.10-glibc2.2](http://packages.ubuntu.com/gutsy/libstdc%2B%2B2.10-glibc2.2)

That got rid of the libstdc++-libc6.2-2.so.3 problem. The next time I tried gv I got a different missing library: "libstdc++-libc6.2-2.so.3". I couldn't find this one in the repositories, but managed to find a copy on the web. I put this in the local gv libraries folder (for me "/usr/chem/gv/lib/"). Note this should be much better than putting it in the system-wide library folder.

Hope that helps!

---

### Post by dufm04 on 2009-01-11
Hi guys. Few days ago, I'm tryimg to install gaussian and gaussview on a hp dv6000 series laptop. First, gaussview not worked, because library libxft1 not was installed. This problem was solutioned with this page: [http://packages.ubuntu.com/dapper/libxft1](http://packages.ubuntu.com/dapper/libxft1). Later, with gaussviwe running, I tested gaussian...But, it's crash, showing the follow error:

[I]Erroneous write during file extend. write -1 instead of 4096
Probably out of disk space.
Write error in NtrExt1: Bad address
Segmentation fault
[/I]
If anyone can help me with it, I would be grateful.

---

### Post by dufm04 on 2009-01-11
Ahhh, and this is not a problem of space on hard disk, I have almost 200GB free, 6GB of swap and 3GB of ram!!

Thanks!!

---

### Post by mfajer on 2009-03-09
> **dufm04 said:**
> Ahhh, and this is not a problem of space on hard disk, I have almost 200GB free, 6GB of swap and 3GB of ram!!

Thanks!!

I had the same problem, and executing the following command as root appears to have fixed the problem.

```

echo 0 > /proc/sys/kernel/randomize_va_space

```

I found this hint here:
[http://www.linuxquestions.org/questions/linux-software-2/how-do-i-get-gaussian-03-a-quantum-chemical-program-to-work-on-fedora-core-5-455395/]("http://www.linuxquestions.org/questions/linux-software-2/how-do-i-get-gaussian-03-a-quantum-chemical-program-to-work-on-fedora-core-5-455395/")

---

### Post by jmaryinchina on 2010-02-23
I think another solution is to add a file in /etc/ld.so.conf, for example gaussian.conf containing /home/me/src/gaussian/lib for example.

---

