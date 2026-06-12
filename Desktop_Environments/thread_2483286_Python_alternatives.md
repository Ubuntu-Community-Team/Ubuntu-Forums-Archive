---
title: "Python alternatives"
date: 2023-01-25
forum: Desktop Environments
---

### Post by grigglestone on 2023-01-25
I have multiple python3 alternatives installed on 22.04LTS. When I select the 3.7 alternative, various programs break e.g. /usr/bin/gnome-terminal .. so I fixed that by changing:

#!/usr/bin/python3

to

#!/usr/bin/python3.10

.. but when the 3.7 alternative is selected, I see a stop icon in the top right (see image). Based on the menu displayed when clicking the icon its something to do with updates (e.g. I see "A problem occurred when checking for the updates."). When I boot with the python 3.10 alternative selected, the icon does not appear so I assume the same fix as above is required elsewhere? Does anyone have any thoughts as to where elsewhere might be?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291633&stc=1[/IMG]

---

### Post by TheFu on 2023-01-25
Ok, so, never, ever, ever, change the python versions installed by the OS.  Don't do it.  There are OS scripts dependent on that exact version and python libraries/modules in the Canonical repos match that expected version.


To have other versions of python on your system, use a python versioning tool.  I think pyenv is one.  [https://realpython.com/intro-to-pyenv/](https://realpython.com/intro-to-pyenv/) This installs whatever version of python you like to somewhere under your HOME. You can install 50 different python versions, each with libraries and modules just for that version.  

Hopefully, someone else, who actually uses python will respond with more details.

I'm a Perl and Ruby guy. They both have similar tools to allow 50 versions of each interpreter to be installed and updated and maintained.  For perl, I use perlbrew.  For ruby, I use rvm.  With  these tools, when I need to deploy an application with a specific version of the interpreter and modules, there's a command to package up everything so it can be moved to pre-prod, tested, then moved to production.

Clear as mud?

1 warning.  If you are like me, you'll forget which version of the language is active and may accidentally run some OS tools with the wrong python found, which can screw the system up.  Be careful.  Once I did an LTS-to-LTS upgrade with the wrong perl being used.  It was ugly and wouldn't boot after finishing.  I had to restore from prior backups to try again. Of course, I didn't realize the version of perl was the problem until later.  Now I have to specifically set the version of perl when I'm using it and use different colors in my terminals so I don't forget which have a custom perl and which are using the default, system-perl.  That might be helpful for your setup, just with python.

---

### Post by mIk3_08 on 2023-01-25
> **grigglestone said:**
> I have multiple python3 alternatives installed on 22.04LTS. When I select the 3.7 alternative, various programs break
22.04 LTS uses the latest python 3.10. Why you have this 3.7?  What is your goal of this python 3.7 and why you have it installed in your 22.04 LTS? Regards and cheers.

---

### Post by TheFu on 2023-01-25
> **mIk3_08 said:**
> 22.04 LTS uses the latest python 3.10. Why you have this 3.7?  What is your goal of this python 3.7 and why you have it installed in your 22.04 LTS? Regards and cheers.

There are many valid reasons for having almost any version of a programming language on a system.  Perhaps the target in production has a specific version and cannot be modified for any number of reasons.  This happens all the time to professional programmers.

---

### Post by monkeybrain20122 on 2023-01-25
If you want to use a different python for development better use a self contained environment like conda instead of messing with system python with update-alternatives. Many system components depend on python to run, the system is set up with a particular version of python and chances are  you'll break things if you use a different system version. 

[https://docs.conda.io/en/latest/](https://docs.conda.io/en/latest/)

If you use conda it  asks to prepend your $PATH and put it in .bashtrc or .profile. If you say yes, you should edit .bashrc (or .profile) afterwards and put /path/to/conda/bin behind $PATH instead of before, that way it won't override the system's python and mess up your system (or you could say no and export that PATH when you start conda)

---

### Post by mIk3_08 on 2023-01-26
> **TheFu said:**
> There are many valid reasons for having almost any version of a programming language on a system.  Perhaps the target in production has a specific version and cannot be modified for any number of reasons.  This happens all the time to professional programmers. Downgrading the python? This will cause damage/conflict to some default running applications since the system is based on python where it uses the default 3.10. If the applications needs a python 3.7 then, the applications needs to be updated before using it to 22.04 LTS system.

---

### Post by Tadaen_Sylvermane on 2023-01-26
> [COLOR=#000000]There are many valid reasons for having almost any version of a programming language on a system. Perhaps the target in production has a specific version and cannot be modified for any number of reasons.

But is there a valid reason other than "just because" that changes make newer version not work with older code? I don't understand why some languages are a moving target. Seems counter productive. Add features all day long. Don't randomly change or destroy old ones just for grins when they did just fine for years. If you insist on mucking about with older working things then make sure it's backwards compatible... Gives me a headache.

Lately I've been learning C and delving into Python. I think Python is to damn complicated if you can never rely on it working the same and it requires an eternal maintenance mode.[/COLOR]

---

### Post by monkeybrain20122 on 2023-01-26
> **mIk3_08 said:**
> Downgrading the python? This will cause damage/conflict to some default running applications since the system is based on python where it uses the default 3.10. If the applications needs a python 3.7 then, the applications needs to be updated before using it to 22.04 LTS system.

The python for development should always be separated from system python. There are times you have to upgrade or downgrade modules and you want to keep things clean. I have separated python for development even if it is the same version as the system python. I have a separated compiled python 3.10 in 22.04, the system version  is 3.10.6, but 3.10.9 in my development python. Not big difference but just to keep things separated. I upgrade and install things in my development environment with pip instead of littering conflicting versions of these modules in my file system.

---

### Post by monkeybrain20122 on 2023-01-26
> **Tadaen_Sylvermane said:**
> But is there a valid reason other than "just because" that changes make newer version not work with older code? I don't understand why some languages are a moving target. Seems counter productive. Add features all day long. Don't randomly change or destroy old ones just for grins when they did just fine for years. If you insist on mucking about with older working things then make sure it's backwards compatible... Gives me a headache.

Lately I've been learning C and delving into Python. I think Python is to damn complicated if you can never rely on it working the same and it requires an eternal maintenance mode.[/COLOR]

I don't know about C, but python uses a lot of modules (numpy, scipy tensorflow etc) which have to be separately installed and imported. They have their own versioning independent of the python version (mostly) and you want to be able to independently upgrade or downgrade these modules. They are typically installed and updated through pip rather than sudo apt install. You don't want to have a lot of these cluttering up your file system, which should be minimal and clean IMO. I guess C doesn't depend so much on external modules and you don't have to modify it once it is installed.

If you don't want to compile python from scratch you can always use a self contained environment like conda [https://docs.conda.io/en/latest/](https://docs.conda.io/en/latest/) or a virtual environment.

---

### Post by TheFu on 2023-01-26
> **mIk3_08 said:**
> Downgrading the python? This will cause damage/conflict to some default running applications since the system is based on python where it uses the default 3.10. If the applications needs a python 3.7 then, the applications needs to be updated before using it to 22.04 LTS system.

Maybe you missed the part about not touching the system python, but using pyenv to have whatever version you need installed? That's in post #2 above.  Using older or newer pythons is separate from the system python and system python modules.

---

### Post by grigglestone on 2023-01-26
I am developing an app that will run on a Raspberry Pi device which supports up to Python 3.7

---

### Post by grigglestone on 2023-01-26
I understand I am playing with fire .. but can anyone tell me what the failing script is?

---

### Post by monkeybrain20122 on 2023-01-26
I think pyenv can only be used to create python virtual environments with the same minor version as the python that creates it. so if you create it with python 3.10.6 (system python for 22.04) it can be only of version 3.10.x. Conda may be more flexible.

Here is what I do, I have multiple python installed in my $HOME. I compiled python from source and invoke each by sourcing a script like


```


export PREFIX=/home/mb/opt/python310
export PYTHONHOME=$PREFIX

export PATH=$PYTHONHOME/bin:$PATH

export LD_LIBRARY_PATH=$PYTHONHOME/lib:$LD_LIBRARY_PATH

export PYTHONUSERBASE=$PYTHONHOME

export PYTHONPATH=$PYTHONHOME/lib/python3.10/site-packages:$PYTHONPATH



```

This way I have maximal flexibility. The script may need some modifications in the future but this contains all major environmental variables and so far it has worked great.

---

### Post by TheFu on 2023-01-26
> **grigglestone said:**
> I understand I am playing with fire .. but can anyone tell me what the failing script is?

There are hundreds, if not thousands, of python scripts used for system management. Your system is a little different than everyone else's, so there's no way for someone to know.  The only solutions are to restore from your backups or do a fresh install.  I get you don't want to read this. 

Learn from this mistake.  

Use 'pyenv' next time you need different python versions for custom development.

---

### Post by monkeybrain20122 on 2023-01-26
> **TheFu said:**
> There are hundreds, if not thousands, of python scripts used for system management. Your system is a little different than everyone else's, so there's no way for someone to know.  The only solutions are to restore from your backups or do a fresh install.  I get you don't want to read this. 
.

 Or he can just to an update-alternatives back to system python and purge python3.7. OP never told us how he installed python3.7, maybe a ppa?

---

### Post by TheFu on 2023-01-26
> **monkeybrain20122 said:**
> Or he can just to an update-alternatives back to system python and purge python3.7. OP never told us how he installed python3.7, maybe a ppa?

What about all the system scripts he manually changed trying to fix the problem?  Those would need to be changed back too. It is is more than a few and linux-fu is not so strong, finding all those would be difficult.  For all we know, he's got Timeshift and it is trivial to move back to a prior OS setup?

I had assumed putting things back was the first thing he tried. Bad assumption grigglestone?

---

### Post by mIk3_08 on 2023-01-26
> **TheFu said:**
> Maybe you missed the part about not touching the system python, but using pyenv to have whatever version you need installed? That's in post #2 above.  Using older or newer pythons is separate from the system python and system python modules.
yeah. I agree with this. using separate environment from your system to your lower version of python will be the right and wise decisions.

> **monkeybrain20122 said:**
> The python for development should  always be separated from system python. There are times you have to  upgrade or downgrade modules and you want to keep things clean. I have  separated python for development even if it is the same version as the  system python. I have a separated compiled python 3.10 in 22.04, the  system version  is 3.10.6, but 3.10.9 in my development python. Not big  difference but just to keep things separated. I upgrade and install  things in my development environment with pip instead of littering  conflicting versions of these modules in my file system.
I agree. Regards ad cheers.

---

