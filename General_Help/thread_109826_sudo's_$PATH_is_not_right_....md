---
title: "sudo's $PATH is not right ..."
date: 2005-12-29
forum: General Help
---

### Post by drfloob on 2005-12-29
How can I change the $PATH variable that sudo uses?  I have my regular user account and root, and both have the same PATH, setup in /etc/profile.  When I use sudo, the PATH is different, missing a few locations, and I can't figure out how to change it specifically.  I thought sudo was supposed to use the user's PATH ...

output:

[me@myPuter~]$ env | grep PATH
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/opt/jdk1.5.0_06/bin:/home/me/bin
[my@myPuter~]$ sudo env | grep PATH
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

I don't consider myself a noob, but I sure feel like one with this issue.  Has someone had this problem, or could you please tell me what's wrong with my setup?  Thanks

---

### Post by Zwack on 2005-12-29
[QUOTE=drfloob]Has someone had this problem, or could you please tell me what's wrong with my setup?  Thanks[/QUOTE]

It is probable that nothing is wrong with your setup.  Sudo cleans up your environment when it is run.  Check your /etc/sudoers file to see if anything is tinkering with your path.  If you want to change it the command to use is visudo (or sudo visudo).  

I hope that this helps,

Z.

---

### Post by drfloob on 2005-12-29
No luck there, Z.  I trimmed it down to 2 lines a few days ago when I first had the problem, just in case.

/etc/sudoers:
root    ALL=(ALL) ALL
%admin  ALL=(ALL) ALL

any other ideas?

---

### Post by Zwack on 2005-12-29
[QUOTE=drfloob]No luck there, Z.  I trimmed it down to 2 lines a few days ago when I first had the problem, just in case.

/etc/sudoers:
root    ALL=(ALL) ALL
%admin  ALL=(ALL) ALL

any other ideas?[/QUOTE]

try this...

echo $PATH
sudo echo $PATH
sudo env | grep $PATH
see if they change...  I get different answers from the bottom one than the top two...

The latter is being run from a shell basically while the top two aren't.

I played around and found the "problem" on my machine...

go look at /etc/profile...  If that doesn't help then let us know.

Z.

---

### Post by drfloob on 2005-12-29
right ... I've done that too.  I backed up /etc/profile and trimmed it down as well a few days ago, still didn't solve my problem.  For your benefit, here's what I've got ...

/etc/profile:
```
export PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/opt/jdk1.5.0_06/bin:/home/me/bin"

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
        . /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi
export TERM=vt100
umask 022

```

and the $PATH tests:

[me@myPuter~]$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/opt/jdk1.5.0_06/bin:/home/me/bin
[me@myPuter~]$ sudo echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/opt/jdk1.5.0_06/bin:/home/me/bin
[me@myPuter~]$ sudo env | grep PATH
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

As far as I understand it, environment varialbes like $PATH are replaced on the command line by the shell before the command is executed, so the first two tests SHOULD be the same.  The third is the only one that shows what PATH sudo is really using.

Mind boggling, isn't it?

Could it possibly be a bug in the sudo package?  I'm using sudo Version 1.6.8.p9-2ubuntu2.1 ... and if it's any help, I did a server install of breezy, but only installed native ubuntu packages ... I haven't compiled anything of my own into it yet.  Also, I've never had a problem like this with any other distro .. I'm a recent ubuntu convert and I REALLY like it otherwise.

---

### Post by Zwack on 2005-12-29
[QUOTE=drfloob]right ... I've done that too.  I backed up /etc/profile and trimmed it down as well a few days ago, still didn't solve my problem.  For your benefit, here's what I've got ...[/QUOTE]

Try sudo -i and see how that works...

Also note 
```
PATH                   Set to a sane value if sudo was configured with
the --with-secure-path option
```
according to the man page...

So I checked /usr/share/doc/sudo/OPTIONS and what do I find...
```
  --with-secure-path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:\
        /sbin:/bin:/usr/X11R6/bin"  

        Give a reasonable default path for commands run as root via sudo.

```

I hope that this helps,

Z.

---

### Post by drfloob on 2005-12-29
"sudo -i" worked for my specific needs this one time ("sudo -i drif", where drif is the script located in my $HOME/bin) ... unfortunately, that's all it seems to work for.  "sudo -i" will log you in to a default shell ... it can't be used to execute binaries, such as "sudo -i env" ... that gives me a "cannot execute binary file" error.

I looked up /usr/share/doc/sudo/OPTIONS ... am I correct in assuming that those were options given at compile time?  I read through the manpage a few times, saw the "sane value" mumbo jumbo in the ENVIRONMENT section, but it makes no mention of how to override this default.  If I could change the value of --with-secure-path, that would work for now, but in a round-about way ... not a permanent solution.

What I need to do is use the user's own PATH in sudo, or possibly more appropriate, use root's PATH.

Thanks for your help so far Z.

---

### Post by Zwack on 2005-12-29
[QUOTE=drfloob]
I looked up /usr/share/doc/sudo/OPTIONS ... am I correct in assuming that those were options given at compile time?  I read through the manpage a few times, saw the "sane value" mumbo jumbo in the ENVIRONMENT section, but it makes no mention of how to override this default.  If I could change the value of --with-secure-path, that would work for now, but in a round-about way ... not a permanent solution.
[/QUOTE]

That's my reading of it too.  It seems that you may need to recompile sudo if you want to keep the PATH.  The only difference you are likely to want to make is that one parameter.  You probably just want to remove the "secure-path"

I hope that this helps. 

Z.

---

### Post by Stokes on 2005-12-29
hi

this is not an error but by intention made like that. the path for 'root' is different than the path for any other users. 'sudo' makes you root for a short time.

following weblink helped me with path-problems:

[http://www.troubleshooters.com/linux/prepostpath.htm#_root]("http://www.troubleshooters.com/linux/prepostpath.htm#_root")

hth
stokes

---

### Post by drfloob on 2005-12-29
well ... I was afraid of that.  Thanks for trying.  I'll keep working on it, see if there's a way around ... what an annoying compile-time option.

Stokes, the sudo path doesn't match the root path either.  I wish it was as simple as that.

---

