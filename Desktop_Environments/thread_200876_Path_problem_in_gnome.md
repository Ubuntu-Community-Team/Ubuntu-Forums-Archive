---
title: "Path problem in gnome"
date: 2006-06-20
forum: Desktop Environments
---

### Post by jazzmuzik on 2006-06-20
In .bash_profile there is a section of code which will add a user bin directory to the path if such a directory exists. Great. The problem is .bash_profile isn't executed from within gnome when you open a terminal, thus no local bin directory in the path.

The solution is to copy the applicable code from .bash_profile to .bashrc. Code example below.

I'm having a hard time understanding how something as essential as this has not been addressed and fixed. The poster below commented on this six months ago.

More information here: [http://dontoddrc.wordpress.com/](http://dontoddrc.wordpress.com/) See the December 20, 2005 note which I'll post below:

> 
December 20, 2005
Adding ~/bin to your path
Filed under: Ubuntu, Tips &#8212; dontoddrc @ 8:42 pm

In Ubuntu, the ~/.bash_profile file adds your ~/bin directory to your path. Putting scripts in your ~/bin directory is convenient because you don&#8217;t have to type the full path to the scripts to run them.

The problem with a default Ubuntu install, however, is that ~/.bash_profile is only for login shells, not for the gnome desktop. So, if you launch a terminal in gnome, ~/.bash_profile doesn&#8217;t get read, and ~/bin isn&#8217;t in your path :( .

The easiest way to fix this is to just copy the lines from ~/.bash_profile to the end of ~/.bashrc:

```
# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
```

Now, whenever you launch a terminal, ~/bin is in your path.



---

### Post by andiii on 2006-08-16
The disadvantage of this is that the Path variable grows bigger and bigger whenever you start a terminal. But I couldn't manage a workaround..

---

### Post by DoctorMO on 2006-08-16
You want to add the path to the main profile /etc/profile and restart your x server, what you want is for the PATH to already have the required directory before you start a terminal.

---

### Post by digidruid on 2006-08-16
I understand that all the options given above does cure the PATH problem, but what I don't understand is the underlying problem of .bash_profile that is not executed when you open a gnome terminal.

Most people will be using gnome terminal when doing whatever they have to do on the cmdline.

Is not executing .bash_profile when opening a gnome terminal
[LIST]
[*]a hard and fast decision by the ubuntu maintainers?
[*]a bug?
[/LIST]

Putting my CVS and other preference environment vars in .bashrc just feels like cheating.

---

### Post by andiii on 2006-08-21
> **DoctorMO said:**
> You want to add the path to the main profile /etc/profile and restart your x server, what you want is for the PATH to already have the required directory before you start a terminal.

That seems to be a workaround at least, thanks!

Putting 

if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

into the profile seems to be a nice solution.

---

