---
title: "Identical Desktops"
date: 2008-05-09
forum: Desktop Environments
---

### Post by btboudreaux on 2008-05-09
I want to customize the Ubuntu desktop so that when a new user logs in, everything is set and customized how I want it to be (not how it come by default). Such as Wallpaper, placement of icons, gnome applets, etc. 

Is there a way to do this?

---

### Post by btboudreaux on 2008-05-10
No one?

I'm trying to get together some documentation on using Ubuntu in the workplace. So far I've gotten Ubuntu to join to an Active Directory domain so users can log in with their domain credentials. I've also gotten members of certain AD groups to be able to use Sudo and SSH with their domain creds. Now I'm working on imaging and trying to see if I can give everyone a customized desktop when they log on.

---

### Post by btboudreaux on 2008-05-11
So if copy all the files in one home folder to another profile, I get all the customized settings from that profile. So where does Ubuntu pull the initial settings from. I think if I edit those settings I can get a customized desktop for every new user logging in. Anyone know?

---

### Post by angry_johnnie on 2008-05-11
Maybe applying changes directly from the root account... It's just a wild guess, really, I haven't done it, but given root's settings seem to be global, it just might do it. :-)

---

### Post by btboudreaux on 2008-05-11
> **angry_johnnie said:**
> Maybe applying changes directly from the root account... It's just a wild guess, really, I haven't done it, but given root's settings seem to be global, it just might do it. :-)

Heh, yeah I already tried that b/c when you sysprep an XP machine, it takes the Administrator profile and builds the Default profile from it. So I thought it might be sort of the same thing with Ubuntu/Linux but that's not the case.

---

### Post by btboudreaux on 2008-05-11
Still no luck

---

### Post by btboudreaux on 2008-05-11
Just bumping it, hoping someone who knows will see this. Still can't find much info on Google etc.

---

### Post by Wolki on 2008-05-12
You might want to take a look at sabayon, it's in the repositories. If you want to lock-down certain parts of the desktop, take a look at pessulus a well.

---

### Post by ephro on 2008-05-12
> **btboudreaux said:**
> Just bumping it, hoping someone who knows will see this. Still can't find much info on Google etc.

Add files to the /etc/profile.d/ directory. Basically you can add whatever you like there and whenever a new account is made it copies the contents of that folder to the new user's home directory. This will allow you to control just about anything you would like.


ephro

---

### Post by btboudreaux on 2008-05-12
> **ephro said:**
> Add files to the /etc/profile.d/ directory. Basically you can add whatever you like there and whenever a new account is made it copies the contents of that folder to the new user's home directory. This will allow you to control just about anything you would like.


ephro

This doesn't seem to be working.

---

### Post by Wolki on 2008-05-12
> **btboudreaux said:**
> This doesn't seem to be working.

Probably because he means /etc/skel/.

Still, for desktop customization and the like for GNOME, sabayon might be the better tool, since it integrates with many things such as gconf and firefox (of course, epiphany as well).

---

### Post by btboudreaux on 2008-05-12
> **Wolki said:**
> Probably because he means /etc/skel/.

Still, for desktop customization and the like for GNOME, sabayon might be the better tool, since it integrates with many things such as gconf and firefox (of course, epiphany as well).

THANKS! That worked! I only want the files that have to do with Background, icons, etc. so I need to do some experimenting. I'll try the sabayon thing too. Thanks again!

---

### Post by ephro on 2008-05-13
> **Wolki said:**
> Probably because he means /etc/skel/.

Still, for desktop customization and the like for GNOME, sabayon might be the better tool, since it integrates with many things such as gconf and firefox (of course, epiphany as well).

Yep, sorry, did mean skel, should have double checked before posting.


ephro

---

### Post by commonplace on 2008-05-13
With Sabayon and Pessulus (both of which I've used), is there a way to have those settings apply to all new profiles that are created? Obviously I wouldn't want it to apply to any admin profiles, so I'd have to create those first, I guess.

What I'm looking for is like what I have in Windows with Active Directory: Some users have locked down profiles, and some don't.

Is this possible? (And if this is too much of a threadjack, let me know and I will create a new thread. I just thought it would be helpful to the OP.)

/Kevin

---

### Post by btboudreaux on 2008-05-13
> **commonplace said:**
> 
What I'm looking for is like what I have in Windows with Active Directory: Some users have locked down profiles, and some don't.
/Kevin

What do  you mean by "locked down profiles?" The admin group is in the Sudo file, so anyone in the admin group will get Sudo rights to the machine. 

If you join Ubuntu to the domain, I found you can add AD groups to the Sudo file so only users in that group have Sudo rights. 

For an AD group you would do it like this:
%DOMAIN\\sudo^users^group ALL=(ALL) ALL

For just a regular domain user it would be:
DOMAIN\\username   ALL=(ALL) ALL

Is this what you were asking? Or was it more along the lines of what menu items show up? Because that I do not know.

---

### Post by commonplace on 2008-05-13
Right, more along the lines of what menu items show up, preventing them from changing the wallpaper, etc. It's in a school situation. We've currently been having each person login using the same account name (everyone logs on as 'student'), but we're wanting to let everyone use their own account. I've used pessulus to lock down what I wanted, and changed permissions for the desktop, but I can't possibly do that for each and every account on each and every computer! I was hoping there was a way to somehow force each new login to 'inherit' everything from an existing profile. I've been researching it pretty heavily, though, and it just flat out doesn't seem possible yet. [Flingpopo.org]("http://www.flingpopo.org/") sounds good, but it's not ready.

/Kevin

---

### Post by btboudreaux on 2008-05-13
If anyone is interested, these are the files I copied to /etc/skel so new users loggin in for the first time can get a customized desktop.

.gconfd
.gconf
.nautilus
.gnome2
.config/menus
.config/autostart
.mozilla (for Firefox customization)

---

### Post by btboudreaux on 2008-05-13
Still some mysteries to solve though.

Where does Ubuntu get the Documents, Music, Pictures, Public, and Videos folders when a new user logs in? And where does it pull the System Menu in gnome from. I found I could customize the Applications Menu by copying .config/menus but this doesn't seem to have an effect on the System menu. And why do Admins have more things in the System menu than regular users.... well I know WHY they have more things, but technically why do they.

By the Way, Thanks for everyone's help. It's been much appreciated!

---

### Post by Wolki on 2008-05-13
> **commonplace said:**
> I've used pessulus to lock down what I wanted, and changed permissions for the desktop, but I can't possibly do that for each and every account on each and every computer!

Open sabayon, choose the profile you want, click the users button and select the users you want to apply this profile to. You can also select all users, which should apply these settings even to users not created yet. If you use these on many computers, you might want to look into sharing home directories between them.

Is this want you wanted? Remember to lock settings you don't want your users to be able to change, including lock-down options.

btboudreaux: honestly, I wouldn't use /etc/skel to pre-set gconf and the like. If you ever want to change the defaults, it's going to be a pain. 

[QUOTE=btboudreaux]Where does Ubuntu get the Documents, Music, Pictures, Public, and Videos folders when a new user logs in?[/QUOTE]

~/.config/user-dirs.dirs

> And why do Admins have more things in the System menu than regular users.... well I know WHY they have more things, but technically why do they.

IIRC the menu is smart enough not to show things that need administrative privileges to users that are not in the admin group. I don't know exactly how the figure that out, might be by looking whether they are started with gksudo or more sophisticated methods.

Everyone interested in this mtopic ight want to take a look at [http://library.gnome.org/admin/](http://library.gnome.org/admin/) , especially [http://library.gnome.org/admin/deployment-guide/](http://library.gnome.org/admin/deployment-guide/)

---

