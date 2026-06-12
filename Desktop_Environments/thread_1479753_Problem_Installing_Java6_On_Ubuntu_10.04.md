---
title: "Problem Installing Java6 On Ubuntu 10.04"
date: 2010-05-11
forum: Desktop Environments
---

### Post by stylishkishore on 2010-05-11
Hello all.
I am new to Linux and new to this beautiful forum.

I am having a problem installing java6 on my Ubuntu 10.04 desktop.
[IMG]http://i43.tinypic.com/27xffaa.jpg[/IMG]

Can anyone please help me.
I already enabled "multiverse". 
Waiting for your reply.Thanks in advance.

---

### Post by QIII on 2010-05-11
The repo you want is the "partner" repo.  Otherwise, you will get Java Update 15, which was so fraught with security issues that Java is up to Update 20.

Add the partner repo to your sources list

```
sudo add-apt-repository “deb http://archive.canonical.com/ lucid  partner”
```

```
sudo apt-get update
```

Then go to Synaptic and search for "sun-java6".  You can pretty much add everything but the 32 bit entry (or, add it if you are running 32 bit).  Don't bother with -source or -javadb unless you plan to do development.

---

### Post by stylishkishore on 2010-05-11
Thanks for quick reply sir.
Actually my intention is to do a project on Servlets and JSP.
When i typed the command 
"sudo add-apt-repository “deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid  partner”

i got an error saying 
 
> Error:Need a repository as argument
What to do sir.I am very basic.

---

### Post by stylishkishore on 2010-05-11
Hello anybody please help me..

---

### Post by wojox on 2010-05-11
This is what I use to install java [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by stylishkishore on 2010-05-11
> **wojox said:**
> This is what I use to install java [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Thank You So Much a wonderful  step by step precedure .**Worked perfect**  for me.

Can you **please give the installation precedures for Apache and tomcat  also**.


Waiting For Your Reply Thanks alot.

---

### Post by wojox on 2010-05-11
Sure just run:

```
sudo tasksel
```

---

### Post by stylishkishore on 2010-05-11
> **wojox said:**
> Sure just run:

```
sudo tasksel
```

Thank you.
When i run command.I get a lot of options.I selected Ubuntu Desktop but nothing done.what to do sir.

---

### Post by wojox on 2010-05-11
Install LAMP Server and Tomcat Server

---

### Post by stylishkishore on 2010-05-11
> **wojox said:**
> Install LAMP Server and Tomcat Server

Can you give me instruction to isntall them on my ubuntu pc?

And also how to set Environment varialble for Java?

---

### Post by wojox on 2010-05-11
Run:

```
sudo taskel
```

When the blue box opens search for LAMP Server and Tomcat. Use the space bar to check those options.

---

### Post by stylishkishore on 2010-05-11
> **wojox said:**
> Run:

```
sudo taskel
```

When the blue box opens search for LAMP Server and Tomcat. Use the space bar to check those options.

Sir, after i executed above command selected tomcat and lamp then it installed fine.But after that it removed all my applications like google chrome, gwibber,adobe air, etc.
And then itshow a black screen with, 
```
starting tomcat---OK
Checking battery status ------


```
After that i restarted my system and checked, no visual ubuntu.Only command prompt asking for username and password.I entered username and password, then also only command view, not visual view.

Here i want to know why it is deleted all my applications? Why the visual appearence gone? 
What is the correct way to install apache tomcat? 
Waiting for your reply sir,

---

### Post by stylishkishore on 2010-05-11
Anyone please help from this problem..

---

### Post by wojox on 2010-05-11
What happens if you 

```
startx
```

You could also try 

```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by QIII on 2010-05-11
stylishkishore --

You probably got an error message on my first suggestion because the  quotation marks were not standard ascii, which is my fault.  

The command should have been

```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid   partner"
```

While wojox' solution worked (and it is what I used for quite some time), it leaves you in a situation where you need to check for updates at Oracle/Sun, remove what you have and reinstall.

Since the packages are now in the Lucid partner repository, when you install it from the repos you get automatic updates along with your normal update process.  Furthermore, the packages are installed where Ubuntu generally installs packages, so it is a normal installation as with anything installed via apt-like installations.  That is what I have done in Lucid.

I'm NOT disparaging wojox!  That was, and still is, a great method for installing Java.  But it has the drawback that you have to keep checking for more recent updates.

If you want to remove it (as instructed in the link wojox gave you), add the partner repository and install Java via Synaptic or apt in the command line, you will not need to check back for updates.  But I'm not saying you have to do that.  You will be very happy with wojox' method.

(wojox -- no offense meant.  It's just available in the repos now.)

---

### Post by stylishkishore on 2010-05-12
I am trying to add environment variable to bashrc file.Here is my file.In that i added the environment variables.But still i am not getting correct output for javac.
Here is my file
```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

export JAVA_HOME="/opt/java/jdk/jdk1.6.0_20"
export PATH=$PATH:$JAVA_HOME/bin
# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
    # We have color support; assume it's compliant with Ecma-48
    # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
    # a case would tend to support setf rather than setaf.)
    color_prompt=yes
    else
    color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi
```

But still not working..What to do..any ideas..plz..

---

### Post by grege on 2010-05-12
The easy way .......

Just open Synaptic go to Settings -> Repositories -> Other Software

The first in the list is lucid partner, tick it then close. Then just reload and it and Sun Java JRE and JDK will appear in the list.

Current version is 6 - 20

Also you only need one java so remove Open JRE/JDK if installed. 

You may have to undo what you have done, good luck.

---

### Post by stylishkishore on 2010-05-12
> **grege said:**
> The easy way .......

Just open Synaptic go to Settings -> Repositories -> Other Software

The first in the list is lucid partner, tick it then close. Then just reload and it and Sun Java JRE and JDK will appear in the list.

Current version is 6 - 20

Also you only need one java so remove Open JRE/JDK if installed. 

You may have to undo what you have done, good luck.
Hey it worked fine.But how to uninstall the open JDK and open JRE?

---

### Post by grege on 2010-05-12
The java you have manually installed in /opt/java can be removed by just deleting the folder. The one you installed from Synaptic will be in /usr/lib/java

Search on Java in Synaptic and see if Open JDK or JRE are installed, just right click and unistall. I am guessing that they are not installed anyway.

---

### Post by stylishkishore on 2010-05-12
> **grege said:**
> The java you have manually installed in /opt/java can be removed by just deleting the folder. The one you installed from Synaptic will be in /usr/lib/java

Search on Java in Synaptic and see if Open JDK or JRE are installed, just right click and unistall. I am guessing that they are not installed anyway.

Okay as you said i just deleted the java that i installed.And uninstalled open java from synaptic.And i checked my java is working now.But i don't know from where it is working.
Now i have to issues.
1.Where is my Sun Java now?
2.How to set JAVA_HOME variable
3.How to set class path

---

### Post by stylishkishore on 2010-05-12
Hello anybody...please help me..

---

### Post by grege on 2010-05-12
Your Java is now in

/usr/lib/jvm/java-6-sun/bin


The way Ubuntu is setup is to have symlinks in /usr/bin that point to links in /etc/alternatives that point to the files in /usr/lib/jvm/java-6-sun which is a symlink to the real java in /usr/lib/jvm/java-6-sun-1.6.0.20

All of this is so it can be updated without changing paths, and so you can change jvms if you want - but the commands java, javac etc are always in /usr/bin

The classpath defaults to the current directory, so you would only need to add to that that for a specific purpose. I have not read all your posts in detail, so are you setting a classpath because you think you have to, or because you need to?

---

### Post by stylishkishore on 2010-05-12
> **grege said:**
> Your Java is now in

/usr/lib/jvm/java-6-sun/bin


The way Ubuntu is setup is to have symlinks in /usr/bin that point to links in /etc/alternatives that point to the files in /usr/lib/jvm/java-6-sun which is a symlink to the real java in /usr/lib/jvm/java-6-sun-1.6.0.20

All of this is so it can be updated without changing paths, and so you can change jvms if you want - but the commands java, javac etc are always in /usr/bin

The classpath defaults to the current directory, so you would only need to add to that that for a specific purpose. I have not read all your posts in detail, so are you setting a classpath because you think you have to, or because you need to?
Hii grege, Thank you so much for taking time and helping me.

As you said, when i went to /usr/lib/jvm/ i found open java1.6.0-open jdk and java-6-openjdk folders rather than sun java folders.
How can i uninstall that open jdk and install sun java?

---

### Post by QIII on 2010-05-12
Uninstall OpenJDK from Synaptic, then go back to my post #15.

---

### Post by stylishkishore on 2010-05-12
> **QIII said:**
> Uninstall OpenJDK from Synaptic, then go back to my post #15.

Okay as you said i uninstalled open jdk from synaptic and checked /usr/bin and there is no more jvm folder.

Now i tried running javac.It is working and tried executing java -version it show me 
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Server VM (build 16.3-b01, mixed mode)

I think this is because i have sun java on /opt/java/jdk/java1.6.0-20. 
Now my doubt is how javac is working? Is it because of /opt/java/jdk or anyother installation ? And if it is because of /opt/java/jdk how to set JAVA_HOME and CLASSPATH variable? 

And i executed the sudo-apt that you prefered me in #15 and it asked me password .i entered.It returned command prompt.

---

### Post by MSPdwalt on 2010-05-13
> **stylishkishore said:**
> Thanks for quick reply sir.
Actually my intention is to do a project on Servlets and JSP.
When i typed the command 
"sudo add-apt-repository “deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid  partner”

i got an error saying 
 

What to do sir.I am very basic.

I had this problem too, delete and manually type the quotes, for some reason when you copy and paste the quotes it pastes in a "different" quotation mark that gnome-terminal doesn't like. I don't fully understand why.

In my limited experience it's better to install as much as you can via you package manager, that way when you apply updates things keep working.

---

### Post by stylishkishore on 2010-05-13
> **stylishkishore said:**
> Okay as you said i uninstalled open jdk from synaptic and checked /usr/bin and there is no more jvm folder.

Now i tried running javac.It is working and tried executing java -version it show me 
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Server VM (build 16.3-b01, mixed mode)

I think this is because i have sun java on /opt/java/jdk/java1.6.0-20. 
Now my doubt is how javac is working? Is it because of /opt/java/jdk or anyother installation ? And if it is because of /opt/java/jdk how to set JAVA_HOME and CLASSPATH variable? 

And i executed the sudo-apt that you prefered me in #15 and it asked me password .i entered.It returned command prompt.

Please need help with this..

---

### Post by grege on 2010-05-13
Open terminal

type

sudo update-alternatives --config java

then

sudo update-alternatives --config javac

Following all of your previous posts I think you now only have one JDK installed - the one you manually installed in /opt

The update alternatives command allows you to set one java to be the default when you have multiple installed.

If you only have one and it works then perhaps you should leave well enough alone.

The only downside is that this way you do not have a java browser plugin. This may or may not be important to your purpose. You can install one manually, but that might take a bit of effort.

So my advice.

Open Synaptic and install only these packages. Ignore all the other javas
 
sun-java6-jre
sun-java6-jdk
sun-java6-fonts
sun-java6-plugin

Then re-run in a terminal

sudo update-alternatives --config java

sudo update-alternatives --config javac

And make sure it is the one in /usr that is the default in both cases.

Then you are setup and ready to go.

---

### Post by stylishkishore on 2010-05-13
> **grege said:**
> Open terminal

type

sudo update-alternatives --config java

then

sudo update-alternatives --config javac

Following all of your previous posts I think you now only have one JDK installed - the one you manually installed in /opt

The update alternatives command allows you to set one java to be the default when you have multiple installed.

If you only have one and it works then perhaps you should leave well enough alone.

The only downside is that this way you do not have a java browser plugin. This may or may not be important to your purpose. You can install one manually, but that might take a bit of effort.

So my advice.

Open Synaptic and install only these packages. Ignore all the other javas
 
sun-java6-jre
sun-java6-jdk
sun-java6-fonts
sun-java6-plugin

Then re-run in a terminal

sudo update-alternatives --config java

sudo update-alternatives --config javac

And make sure it is the one in /usr that is the default in both cases.

Then you are setup and ready to go.

Thank you so much.Now i checked.It is the only java i have in /opt/java/jdk/
Now i want to check my JAVA_HOME variable and Classpath variable.How to check it?

---

### Post by grege on 2010-05-13
As sudo edit /etc/environment and put these lines at the end

JAVA_HOME="/opt/java/jdk/java1.6.0-20"
CLASSPATH="/opt/java/jdk/java1.6.0-20/lib:."

save then log out and back in again

check opening a terminal and typing 

echo $JAVA_HOME
echo $CLASSPATH

I am only guessing the CLASSPATH path as mine is setup using Java installed from Synaptic, it should be close enough so you can work it out yourself.

---

### Post by stylishkishore on 2010-05-13
Thank you so much grege.Finally, how to start my apache tomcat.It is at usr/local/apache-tomcat.
I used sh /usr/local/apache-tomcat/bin/startup.sh
 it give me the output,
```

Using CATALINA_BASE:   /usr/local/apache-tomcat
Using CATALINA_HOME:   /usr/local/apache-tomcat
Using CATALINA_TMPDIR: /usr/local/apache-tomcat/temp
Using JRE_HOME:        /opt/java/jdk/jdk1.6.0_20
Using CLASSPATH:       /usr/local/apache-tomcat/bin/bootstrap.jar
touch: cannot touch `/usr/local/apache-tomcat/logs/catalina.out': Permission denied
/usr/local/apache-tomcat/bin/catalina.sh: 448: cannot create /usr/local/apache-tomcat/logs/catalina.out: Permission denied


```Is it the correct way to start it..or any other way.

---

### Post by grege on 2010-05-13
I know nothing about Apache, however one observation - in Linux you should put a dot at the beginning of a command, to make that the working directory. 

So instead of

sh /usr/local/apache-tomcat/bin/startup.sh

try

sh ./usr/local/apache-tomcat/bin/startup.sh

If that does not help you have permissions problems. Try running temporarily as root by starting with sudo - but you must not leave it like that as it would be too insecure.

At this point you need an Apache expert.

---

### Post by stylishkishore on 2010-05-13
thanks alot grege..common apache experts fix me..plz..

---

### Post by stylishkishore on 2010-05-13
> **stylishkishore said:**
> Thank you so much grege.Finally, how to start my apache tomcat.It is at usr/local/apache-tomcat.
I used sh /usr/local/apache-tomcat/bin/startup.sh
 it give me the output,
```

Using CATALINA_BASE:   /usr/local/apache-tomcat
Using CATALINA_HOME:   /usr/local/apache-tomcat
Using CATALINA_TMPDIR: /usr/local/apache-tomcat/temp
Using JRE_HOME:        /opt/java/jdk/jdk1.6.0_20
Using CLASSPATH:       /usr/local/apache-tomcat/bin/bootstrap.jar
touch: cannot touch `/usr/local/apache-tomcat/logs/catalina.out': Permission denied
/usr/local/apache-tomcat/bin/catalina.sh: 448: cannot create /usr/local/apache-tomcat/logs/catalina.out: Permission denied


```Is it the correct way to start it..or any other way.
Hey anyone to help me ..this

---

