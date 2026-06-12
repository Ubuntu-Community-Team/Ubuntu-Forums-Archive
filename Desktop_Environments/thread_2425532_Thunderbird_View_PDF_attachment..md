---
title: "Thunderbird View PDF attachment."
date: 2019-08-26
forum: Desktop Environments
---

### Post by rsteinmetz70112 on 2019-08-26
When using Thunderbird if I want to view a PDF attachment when I click on the attachment Thunderbird asks if I want to view the file using "Document Viewer" I say OK and nothing happens. When I select "Other" I get a list showing me an PDF icon with the name "Document Viewer", what program is that? I can't find it.

If I save the Attachment and try to open it the default is still Document Viewer and it still doesn't open. I get no error or any indication of what is wrong.

I think the acutal package is evince, and according to dpkg the latest version is installed and configured.

---

### Post by Artim on 2019-08-27
Is thias Ubuntu or Lubuntu or Xubuntu or Kubuntu?  They have different ways of dealing with this.  Please tell us what OS you're using!

---

### Post by TheFu on 2019-08-27
Might it be another snapd workflow problem?  Snaps run inside a sandbox and have to be specifically given permission to use any helper programs.

BTW, 'atril' is a fork of evince, that is what my 16.04 desktops have.

I don't allow direct launching of any programs from any other high-risk program.  Call it a security step to save attachments to a temporary location first.

---

### Post by rsteinmetz70112 on 2019-08-27
Operating system Ubuntu 18.04 LTS

'atril' is not installed.

'evince' is installed but will not launch even with a saved file.

---

### Post by SeijiSensei on 2019-08-27
Edit > Preferences > Attachments lets you specify the default viewer for different types of files.

---

### Post by deadflowr on 2019-08-27
Does Document Viewer (evince) open from the menu system?
What happens if you try launching it from the terminal?
The command *evince* will start it up.

There is a snap version of evince, but you would have had to install it yourself,
and I'm not sure you would have since evince' apt version is a default program for Ubuntu.
(Same applies to thunderbird)

Unless, maybe, you installed from the Ubuntu minimal setup option in the installer, which cuts out a bunch of stuff.
I do not know what exactly is cut, though.
But if you did use that method to install Ubuntu, Using the software store to install these packages it can mix snap and apt packages, 
so it'd be easy to install the snap version without realizing it.

---

### Post by rsteinmetz70112 on 2019-08-27
> **deadflowr said:**
> Does Document Viewer (evince) open from the menu system?

I don't see it in the menus.

> What happens if you try launching it from the terminal?
The command *evince* will start it up.

I haven't tried that I will try it when I get home this evening.

> There is a snap version of evince, but you would have had to install it yourself,
and I'm not sure you would have since evince' apt version is a default program for Ubuntu.
(Same applies to thunderbird)

This was release upgrade from 16.04 LTS.  It should have all of the default installs. I did try to install 'evince' it with apt but was told the latest version was already installed. 

> Unless, maybe, you installed from the Ubuntu minimal setup option in the installer, which cuts out a bunch of stuff.
I do not know what exactly is cut, though.
But if you did use that method to install Ubuntu, Using the software store to install these packages it can mix snap and apt packages, 
so it'd be easy to install the snap version without realizing it.
I didn't do a minimal install, and I never use the Software Store. I prefer synaptic and apt.

---

### Post by deadflowr on 2019-08-27
Perhaps try a purge and reinstall of evince.
Maybe double check your home directory too to see if any evince folders are there.
They'd most likely be in the .cache and .config directories.
I'd do the double check just to make sure nothing in your home folder is causing issues. Or could be causing the issues.

> I didn't do a minimal install, and I never use the Software Store. I prefer synaptic and apt.
I didn't really think you did. It was a just in case scenario.
FTR: the minimal I refer to is this: [https://www.omgubuntu.co.uk/2018/02/ubuntu-18-04-minimal-install-option]("https://www.omgubuntu.co.uk/2018/02/ubuntu-18-04-minimal-install-option")
People tend to confuse this method with the [minimal cd method]("https://help.ubuntu.com/community/Installation/MinimalCD") (or also known as netinstall ) which is a different beast entirely.
But that's more or less a moot point since it doesn't affect this issue.

---

### Post by rsteinmetz70112 on 2019-08-27
OK I'm back at the house. I found evince in the menus. It doesn't start

I tried from a terminal window and got this:

```
$ evince
No protocol specified
Unable to init server: Could not connect: Connection refused
Cannot parse arguments: Cannot open display: 
```

Obviously something is messed up.

Running 

```
# find -name evince 
./.config/evince
# ls -ld .config
drwxr-xr-x 42 rob rob 4096 Aug 26 21:18 .config
# cd .config
# ls -ld evince
drwx------ 2 rob rob 4096 May 12 09:44 evince
# 
```

Not sure what those are supposed to be.

I tried:
```
# apt purge evince
# apt install evince
```
both ran without error - no joy.

I tried another user and it works in that user. Now to figure out what the difference is.

---

### Post by TheFu on 2019-08-27
Are you running as root?  Best not to run GUI programs as root or with a normal sudo {program}.  It will mess up all sorts of things.

---

### Post by rsteinmetz70112 on 2019-08-28
I'm not running as root. The gnome session is as my user. I've only run sudo in a terminal session to check out things and to remove and install evince.

I've tried all of this as a normal user with the same result. See the first code and error messages in the previous post, evince won't start as this user or in this users terminal session but will start as a different user.

---

### Post by TheFu on 2019-08-28
If it works under a different userid, but not your normal one, that would mean to me there is a permissions issue, probably in the ~/.config/ directories, probably due to using sudo.

```
$ find ~/ -user root -print
```
should find the files.  Might look for files owned by any different user, 
```
$ find      ~/      ! -user $USER       -ls
```
will show the permissions, owner and group.

Just a guess, but it happens lots of times in these forums.

---

### Post by rsteinmetz70112 on 2019-08-28
I also suspect it's a permissions issues, although I've checked the permissions on the ~/.config/evince files in both users home directory and they are the same.

I'll have to put this aside for a while I leaving on a trip and won't be back for over a week.

Thanks for all of the help.

---

### Post by TheFu on 2019-08-28
Ah ... perhaps comparing the evince config file between the 2 different userids will shine some light on the issue?

---

