---
title: "Where to set environment variables?"
date: 2004-10-31
forum: Desktop Environments
---

### Post by Bob Collins on 2004-10-31
This must have been asked before, but both searches on this list and google didn't reveal the answer. To what file do I add environment variables, both for all users and on a per-user basis.

The way I understood was to add system (all users) info in /etc/profile and per-user info in ~/.profile (or ~/.bash_profile?). Neither appear to be called by Ubuntu.

The Gnome developers, in there documentation, think the profile files should be sourced by /etc/gdm/Xsession but Ubuntu's configuration doesn't follow Gnome's model.

So... if I want to follow the Ubuntu way, where do I set variables?

Thanks,

Bob Collins
Sunnyvale CA USA

---

### Post by jdong on 2004-10-31
[QUOTE=Bob Collins]This must have been asked before, but both searches on this list and google didn't reveal the answer. To what file do I add environment variables, both for all users and on a per-user basis.

The way I understood was to add system (all users) info in /etc/profile and per-user info in ~/.profile (or ~/.bash_profile?). Neither appear to be called by Ubuntu.

The Gnome developers, in there documentation, think the profile files should be sourced by /etc/gdm/Xsession but Ubuntu's configuration doesn't follow Gnome's model.

So... if I want to follow the Ubuntu way, where do I set variables?

Thanks,

Bob Collins
Sunnyvale CA USA[/QUOTE]


The **/etc/environment** file. profile files require that you use **export** to set the variables; the environment file doesn't.

---

### Post by Bob Collins on 2004-10-31
Thanks, that works. BTW, do you know where the /etc/environment file is sourced?
Just curious.

Bob Collins


BTW, thanks for the quick reply. You and this forum are a great help. Now if the Java install was a bit saner....

---

### Post by jdong on 2004-10-31
[QUOTE=Bob Collins]Thanks, that works. BTW, do you know where the /etc/environment file is sourced?
Just curious.

Bob Collins


BTW, thanks for the quick reply. You and this forum are a great help. Now if the Java install was a bit saner....[/QUOTE]

Use the whole java-package shebang... it works for me

---

### Post by offby1 on 2004-12-26
[QUOTE=jdong]The **/etc/environment** file. profile files require that you use **export** to set the variables; the environment file doesn't.[/QUOTE]

I'd like to ask about this -- this seems to be very nonstandard, and judging by some of the threads I've seen on the subject, as well as my own experience, this is extremely confusing to some users coming to Ubuntu from other distributions.

Can someone explain the rationale behind this deviation from standard practice to me?  And also, as was asked above, where is /etc/environment sourced?  Can I set LD_LIBRARY_PATH there, as well?  I keep hearing horror stories about trying to make that work.

---

### Post by sahand on 2005-01-08
[QUOTE=offby1]I'd like to ask about this -- this seems to be very nonstandard, and judging by some of the threads I've seen on the subject, as well as my own experience, this is extremely confusing to some users coming to Ubuntu from other distributions.

Can someone explain the rationale behind this deviation from standard practice to me?  And also, as was asked above, where is /etc/environment sourced?  Can I set LD_LIBRARY_PATH there, as well?  I keep hearing horror stories about trying to make that work.[/QUOTE]

Ok I have been searching all over the internet for similar reasons, I mean just
recently I have found out about this environment file to set env variables.

So far I have had similar problems in Agnula/Demudi, I couldn't understand how to set
my env variables.

As a note putting your env var in your bash file whether it be your .bashrc files
or creating a profile.d dir in /etc you can't expect to have the env var exported
unless you do it manually, for some reason they don't get called.
I don't know why...

Could some one correct me here or tell me why?

If I ssh into my comp or if I
$sudo su -
or if I simply
$su - <myusername>
all those env var that I have set in my file bashrc or profile.d dir are now picked up.

I have read about debians policy thing about env var, and how programs should
instead make wrappers for their bin dir instead of setting the $PATH env var or
something like that, but I can't quite remember it because my issue was not that
but it was to set my JAVA_HOME env var as using jave in the past I know that that
is required for some applicationgs.

Well yeah now I know that putting it in /etc/environment it will be picked.

I also want to know what was the reasons made in making such a choice for
environment variables.

Well I hope I have helped a little.

Regards,

Sahand

---

### Post by sahand on 2005-01-08
By the way there also is a file
/etc/login.defs

---

### Post by prahal on 2005-02-08
I think ubuntu carry debian heritage regarding PATH definition. It is overwritten by every daemon, program, layer ( cron, bash, login, pam_env all happily overwrite each other settings and especially administrator ones).
If you look in the bTS you ll see that some say its about security (though a secure "which" is more appropriate ...) or to avoid breakage ... (that s pretty unfirendly) . Finaly there seems to be battle between bash/base_files (/etc/skeleton) and a few other so to have THEIR PATH setting working  they hardcode the one they like.


PATH is the only problem. All other environment variables are preserved (which is not the case in most other distribution, except for things like su where there is still discussion about what should be inherited).
It seems that pam_env could help fix that and avoid this mess. The problem is that it does not have an option to set a root PATH different than the other users one.
I am looking after that as my opinion is that extending pam_env to support that is much less work than managing the current mess in debian. But it may not be implmentable in it . Then maybe a pam_rootenv would be a good thing


/etc/environment cannot be sourced. Redhat and gnome are wrong. IF you source it you have to add "export" and other shells commands. As other tools using it (ssh , login, all applications using pam_env) expect a VAR=VALUE list , those shell commands (export) break the parsing .

/etc/profile is only for shells (nearly bourne shells only).
/etc/login.defs is only for the login program (shell only).
/etc/X11/Xsession.d for X11 sessions (xdm, kdm, gdm).

If your /etc/environment is correct , it is a great place to put JAVA_HOME, LD_LIBRARY_PATH and such.for system wide usage. But you cannot use variable inside it , it is not interpreted by a shell. FOr this you could use pam_env module , configured in /etc/security/pam_env.conf though not all environment variable are defined when it is executed. Environment variables setted in profile files or other applications specific configuration are usually executed after pam_env.
PS: the reason it was designed this simple is for it to become shell/application agnostic.

For PATH things a few examples:
- if login from the console: set it in /etc/profile (for root you have to do it in /root/.profile or /root/.bash_profile).
NB : if bash_profile exists profile is not read. this is a xor. cf man bash.
- if login from GDM,kdm, xdm :
they all source /etc/X11/Xsession.d files in a shell. You can add a new one and export variables , do test in shell language.
If you xant to only affect one of them, they ahve specific configuraitons too :
  [http://www.jirka.org/gdm-documentation/x241.html](http://www.jirka.org/gdm-documentation/x241.html)
for gdm PreSession is the one. 
/etc/X11/Xsession.d are recommanded.
- and other : ssh, ftp, apache, php ,.cron ... require specific setup too.


The good news is that all xsessions can now be managed by /etc/X11/Xsession.d, a few monthes ago each x login manager had its own version of those files.


NB: there are no equivalent of /etc/environment for user (like ~/.env ). To set the PATH for one user only require to setup each application separetely.  Note that X session does not have "user profile" like configuration files. You can create a file with :

if [ $HOME/.xprofile ];then
  . $HOME/.xprofile
fi

in /etc/X11/Xsession.d to have one.

m17n-env debian package etup something liek that (but it can manage executing user defined scripts too).

---

### Post by mrmaple on 2005-04-16
I'm not having any luck with environment.

First, I realized when X didn't start that you can't do PATH=$PATH:/mystuff
and then once I guessed at a reasonable path, my LD_LIBRARY_PATH would not set.  (all my other variables were fine, but LD_LIBRARY_PATH is getting trounced somewhere else.  (I'm using hoary)

Where else can I put my environment varibales?

-Jim

---

### Post by pawel.z on 2005-05-20
This is just for gnome.
  $ cat /etc/X11/Xsession.d/55gnome-session_gnomerc
So it seems you can put your env variables to ~/.gnomerc; eg.
  export ANT_HOME=$HOME/development/java/libraries/ant 
  export PATH=$PATH:$ANT_HOME/bin
This is just for user specific. Globally I suggest /etc/environment or
you could probably use /etc/X11/Xsession.d/55gnome-session_gnomerc
for this purpose.

---

### Post by hadarot on 2005-07-08
Concerning the issue of setting environment variables by having bash read /etc/profile and ~/.bash_profile, and concerning bash not reading these files when when logging in via an X display manager, in contrast to logging in via a console:
 
When bash is invoked as an interactive shell, the file(s) it reads depends on whether or not it is a login shell. A *login* interactive shell first reads /etc/profile, if it exists, and then reads ~/.bash_profile (or ~/.bash_login, or ~/.profile, which ever comes first).  In contrast, an interactive *non-login* shell simply reads .bashrc, if it exists.    Now, when you start a bash shell by logging into a console, this consitutes starting a *login* shell, which hence reads /etc/profile and then ~/.bash_profile. (A login shell does NOT automatically read ~/.bashrc, which is why you want to source this file from ~/.bash_profile.)  On the other hand, when starting a shell after you have *already* logged in, whether via the console of through an X display manager, that shell will be non-login, and hence will only read ~/.bashrc.  (For more details on this, please consult the Bash manual at [http://www.gnu.org/software/bash/manual/bashref.html#SEC65)](http://www.gnu.org/software/bash/manual/bashref.html#SEC65)).
 
But then how does one ensure that /etc/profile and ~/.bach_profile are procssed when you log in via an X display manager.  Sometimes the /etc/X11/xfm/XSession script will be configured ot ensure htis. But when it is not, the best way to resolve this issue is as follows (taken from [http://wiki.arslinux.com/Environment_Variables](http://wiki.arslinux.com/Environment_Variables)) 
 
X Login
If a user logs in via one of the X display managers (xdm, kdm, gdm), then that user's .bash_profile won't get run, because the system never starts the shell, bash, that reads it. Instead, when you log in, the display manager will start whatever window manager you use, by running /etc/X11/xdm/Xsession with a parameter representing your choice. 
If you need to set specific environment variables on a permanent basis with a graphical login, you'll instead want to create a ~/.xsession file; if that file is present, the main Xsession will pass control of to it instead of executing a window manager directly. 

What you'll want to do is make it a bash script (text file that starts with #!/bin/bash and is marked executable), which has a few export lines like above to set your environment up, and then uses the "exec" command to run your window-manager-of-choice. 

Of course, if there's anything else you want to do on login (such as running a set of your favorite X programs), you can stick it there as well. 

Thus, one should create an execuatble ~/.xsession bash script, and within it source /etc/profile, then ~/.bash_profile (the latter of which should itself source ~/.bashrc), then exec to the window manager that you use. You ~/.xsession file can be made much more complex, depending on how you want to customize your X login session. Do some more homework and internet searching for more info on customizing this file...  (Here is one example, or many: [http://www.phildev.net/linux/x.html](http://www.phildev.net/linux/x.html))

---

### Post by joshuapurcell on 2005-07-24
The only way that I've been able to get the added environment variables to work in all terminal (gdm, whatever) is by adding the needed lines to **/etc/bash.bashrc**. I've tried adding the export lines to /etc/profile, /etc/environment, ~/.bashrc, and ~/.bash_profile, but none of those files have made it so that I can use my environment variables in any terminal I open.

---

### Post by blanca on 2005-08-04
I have set them in  .bashrc file and it works. This is what I added:


# User specific environment and startup programs
JAVA=/usr/local/j2sdk1.4.2_08/bin/
WEKAHOME=/home/blanca/weka-3-4-5
PATH=$PATH:$HOME/bin:$JAVA:$WEKAHOME
export PLAYERPATH=/usr/local/lib
export CLASSPATH=/home/blanca/weka-3-4-5/weka.jar:$CLASSPATH

---

### Post by gevoelig on 2005-09-06
One thing I don't understand is why setting X environment variables has to be so hard (i.e. a simple configuration option like "add (user) envrionment variable"  in the session preferences would be so much easier.)

Regards,

G.J.

---

### Post by anindya_m on 2005-10-04
Hi. This is a quick fix, but I found that (for bash) if you simply add the line:
. ~/.bash_profile
in the file /etc/gdm/Xsession it  works. The location where you add the line is important, as that particular code section needs to be executed. I add it right before the comment:
# this will go into the .xsession-errors along with all other echo's
and it works. Hope this will help.

regards,
Anindya

---

### Post by gevoelig on 2005-10-04
Thanks anindya_m! That solved the problem.

I still think a user-dialog in which environment all possible variables (in all possible files) can be set would be very handy. 

regards,

G.J.

---

### Post by NeTo on 2005-10-17
I'm having a headache trying to add paths to LD_LIBRARY_PATH for all users.

Say I want to set, for example:```
LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/my_path
```I have created a script in /etc/X11/Xsession.d with that line, I have also added it to /etc/bash.bashrc

Now, if in a terminal I do:```
echo $LD_LIBRARY_PATH
```, the variable appears with its expected value. If I run a program from the terminal that uses a lib in /usr/local/my_path it runs correctly.

**However**, if I run this script from Gnome (for example, using 'Run application'):```
#!/bin/sh

echo $LD_LIBRARY_PATH > uhm.txt
```The file ends up blank, meaning LD_LIBRARY PATH wasn't set.

If instead of using LD_LIBRARY_PATH i set/use PATH as the variable (or any other variable name) everything works correctly. This odd behaviour seems spicific to LD_LIBRARY_PATH

What am I doing wrong?

---

### Post by NeTo on 2005-11-14
After some struggling I have finally found a solution that suits me for setting environment variables globally. I will explain it briefly:

For anything but $LD_LIBRARY_PATH, I have created a small file, /etc/neto_env , that will hold all the environment variables I want to set. So, the file looks like:```
# NeTo's environment variables.
# Sourced by:
# /etc/bash.bashrc (for interactive non-login shells)
# /etc/X11/Xsession.d/55neto_env (for Xsessions)

# Set JAVA_HOME
export JAVA_HOME="/usr/lib/j2sdk1.5-sun"

# Add gEDA to the path
PATH=$PATH:/usr/local/geda/bin
```Then I sourced the file in /etc/bash.bashrc and /etc/X11/Xsession.d/55neto_env by adding the following line to those files:```
# Add NeTo's environment variables
. /etc/neto_env
```

Now, if I want to change a environment variable, I just need to edit /etc/neto_env , and the changes will apply to bash and X sessions.

For $LD_LIBRARY_PATH, my solution was way different. I'm simply not using the variable at all. To add a directory to the library cache, the command```
sudo ldconfig -v <some_path>
``` gets the work done :D

I wanted to share this, because 1) I'm not sure if it is the right way to handle this situation, and 2) It may be helpful, especially for Linux newcomers like me.

---

### Post by mfyahya on 2005-11-15
[QUOTE=blanca]I have set them in  .bashrc file and it works. This is what I added:


# User specific environment and startup programs
JAVA=/usr/local/j2sdk1.4.2_08/bin/
WEKAHOME=/home/blanca/weka-3-4-5
PATH=$PATH:$HOME/bin:$JAVA:$WEKAHOME
export PLAYERPATH=/usr/local/lib
export CLASSPATH=/home/blanca/weka-3-4-5/weka.jar:$CLASSPATH[/QUOTE]

There's a small problem with this approach. If you type bash in a console to start a new instance of bash, .bashrc will be sourced again and the PATH variable will grow and have $HOME,  $JAVA and $WEKAHOME defined twice. I don't know if this can cause any problems or not, but it's not nice behavior imho.

---

### Post by NeTo on 2005-11-15
What if you change it to the following?:```
# Check if variables have been already set by this script
if [ -z "$MY_OWN_ENV" ]; then
export MY_OWN_ENV=1

# User specific environment and startup programs
JAVA=/usr/local/j2sdk1.4.2_08/bin/
WEKAHOME=/home/blanca/weka-3-4-5
PATH=$PATH:$HOME/bin:$JAVA:$WEKAHOME
export PLAYERPATH=/usr/local/lib
export CLASSPATH=/home/blanca/weka-3-4-5/weka.jar:$CLASSPATH

fi
```

---

### Post by daodao on 2006-01-30
I tried NeTo's suggestions and they worked great.  Now both my log-in and non-log in terminal have the path variable set to my customized version.

I do have a problem though: when I run a command with sudo the $PATH variable appears not to be used.  sudo echo $PATH produces the expected result, but if I run sudo *cmd* where *cmd* is a command that resides in the custom path, the command isn't found.  The command is found when I'm not sudoing, yet, the $PATH values are identical whether I'm sudoing or not.  What's going on???

---

### Post by NeTo on 2006-01-31
That's most likely because the value $PATH of path gets replaced before running   sudo. For example if you run:```
a='echo test'
sudo $a
```You will see *test* displayed in stdout.

Furthermore, you can run```
sudo bash
echo $PATH
``` to see what's the value of $PATH when you're using sudo. BTW, type ```
exit
``` to return to the previous bash session.

Unfortunately, I'm not sure what's going wrong in your case. I hope the above can be useful as a guideline though.

---

### Post by daodao on 2006-02-01
NeTo,

Thanks for the quick reply.  You are definitely right about the sudo'ed versions using a different PATH variable.  It looks like so:

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

Perhaps the final X11R6 folder is clue for someone more knowledgeable than I?  This, by the way, looks nothing like the search path I'm using.  By the way, right now I'm sourcing the little chunk of code:

```
if [ -z "$MY_OWN_ENV" ]; then
export MY_OWN_ENV=1
PATH=$PATH:/usr/local/mysql/bin:.
fi

```

in /etc/bash.bashrc and /etc/X11/Xsession.d/my_env.  Any ideas about why this works for both login and non-login sessions, but fails the instant I su or sudo?

---

### Post by fraction on 2006-02-14
Another thank you going out to Neto - [post 18](http://ubuntuforums.org/showpost.php?p=493027&postcount=18) did it for me.

Perhaps this should be in the wiki. I expect there's plenty of people out there who found this as irritating as me.

---

### Post by NeTo on 2006-02-14
> **daodao]Any ideas about why this works for both login and non-login sessions, but fails the instant I su or sudo?[/QUOTE]

I think it is because $MY_OWN_ENV is preserved when you run sudo, but $PATH isn't. I gave it a though, and came out with this:```
CURR_ID=`id -u`
if [ -z `echo $MY_OWN_ENV_ID|grep :$CURR_ID` ] said:**
> 
Perhaps this should be in the wiki. I expect there's plenty of people out there who found this as irritating as me.
I agree. I will crate an account later on and see what I can do.

---

### Post by Caveira2099 on 2006-05-25
Hi everyone!

I was trying to install Lahey Fortran but its installation scripts failled with environment variables. I was starting to think about destroying my valuable LF95 cd when I finally found this post.

I simply added the setup command to .bashrc (at the end of it) and it worked fine.

```

# Call LF95 shell setup script.
. /usr/local/lf9562/bash_setup
```

And I agree with a sugestion I saw here... This should be noted on the wiki or anywhere else people could find this information. I have spent some time on google for nothing...

Thanks again!

Best regards,

---

