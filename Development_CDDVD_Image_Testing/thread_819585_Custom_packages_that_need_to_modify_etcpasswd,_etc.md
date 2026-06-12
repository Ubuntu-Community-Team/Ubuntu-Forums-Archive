---
title: "Custom packages that need to modify /etc/passwd, /etc/group, etc."
date: 2008-06-05
forum: Development CD/DVD Image Testing
---

### Post by pocketchange on 2008-06-05
I'm currently working on creating a custom alternate install using UCK.  Part of my requirements is that I have a custom NIS package.  I want to modify the following files to include the "+" entry at the end for compat:

/etc/passwd
/etc/group
/etc/shadow

I also need to modify the /etc/nsswitch file with the following:

passwd:  cache compat
group:   cache compat
shadow:  cache compat

I can modify the yp.conf file by doing the following:

[LIST=1]
[*]sudo apt-get install nis
[*]<modify yp.conf and test>
[*]dpkg-repack nis
[/LIST]

this results in a version of nis that contains a custom yp.conf.  I tried to figure out which package has the /etc/passwd, /etc/shadow, and /etc/group files so I can modify it similarly, but I have no idea which to change.  Is there a best practice to modifying these files?  Should I create a postinstall script that appends these?

Thanks for the suggestions.

---

### Post by chrisccoulson on 2008-06-19
> **pocketchange said:**
> 
this results in a version of nis that contains a custom yp.conf.  I tried to figure out which package has the /etc/passwd, /etc/shadow, and /etc/group files so I can modify it similarly, but I have no idea which to change.  Is there a best practice to modifying these files?  Should I create a postinstall script that appends these?

Those files don't belong to any package, as they're part of the base install. I'm not sure what you're trying to achieve, but you should probably modify them using a postinst script as you've already suggested. Try to use the correct tools for modifying them (adduser, addgroup, usermod, groupmod, passwd etc...) as opposed to directly modifying them with a script, as you're less likely to break your system. If you use the script to edit them directly, make sure that your script backs them all up first

---

### Post by pocketchange on 2008-06-19
Thanks for the recommendation.  What I'm specifically trying to do is use the "+" entries in the /etc/passwd file.  At an office with Bob and Larry where, say, Larry is a jerk, I can modify my /etc/passwd with these entries:


```
+bob
-larry
```


This effectively allows (+) bob to login and denies (-) access to Larry.  I have a few default entries I'd like to add to the /etc/passwd, /etc/group, and /etc/shadow.  One example is adding +@admins netgroup (@) to the /etc/passwd file so that all admins are allowed (+) to login by default.

I would like all of this in a package, say, "nis-3.17-XmysiteY.deb", where:

X = the ubuntu version (version 1 in this case)
Y = my own custom package version

(Is it bad to just use "mysite"?  I noticed lintian complains every time.)

The package would install NIS, install a default yp.conf tailored to my needs, append the "+@admins" entry to /etc/passwd and modify the /etc/nsswitch.conf to 


```
passwd: compat
group: compat
shadow: compat
netgroup: files nis
```


So the other big question is this, how's the best way to modify an /etc file?  I currently have a script with this line in it:

```

sed -i.bak`date +'%Y%m%d'` -e 's/passwd:\(.*\)files nis$/passwd:\t\tcompat/;s/group:\(.*\)files nis$/group:\t\tcompat/;s/shadow:\(.*\)files nis$/shadow:\t\tcompat/;s/netgroup:\(.*\)files$/netgroup:\tfiles nis/' nsswitch.conf
```


Is this something better done with diff?  This makes assumptions about what is in the file?  If the user had "passwd: files" instead of "passwd: files nis", then this script breaks.  Would diff break too?  I don't know that I should just create my own nsswitch.conf because I don't want to trample over the user's settings...

---

### Post by pocketchange on 2008-06-20
chrisccoulson,

I did some more reading through the Debian Policy and you are correct.  It says to use the appropriate program in a post-init script to modify the files.  

I found the program for nsswitch called auth-client-config that you invoke from the postinst to modify the nsswitch.conf file.  Here's the link:

[https://wiki.ubuntu.com/AuthClientConfig](https://wiki.ubuntu.com/AuthClientConfig)

I've been digging through the adduser command, but it doesn't appear to support the "+username" entries.  I even tried with --force-badname and it doesn't appear to work.  I get this:

```
adduser: To avoid problems, the username should consist only of
letters, digits, underscores, periods, at signs and dashes, and not start with
a dash (as defined by IEEE Std 1003.1-2001). For compatibility with Samba
machine accounts $ is also supported at the end of the username
zsh: exit 1     sudo adduser "\+blah" --force-badname
```

I had more success with the "useradd" command but there's no way to force it to omit the home and shell entirely.  So far it's looking like Debian/Ubuntu have no means of creating the + entries through a script.

---

