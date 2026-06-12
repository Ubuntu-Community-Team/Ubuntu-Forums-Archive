---
title: "Deployment on school netbooks."
date: 2011-02-07
forum: Desktop Environments
---

### Post by chrismyers on 2011-02-07
Hi there guys & gals,

I'm a school admin & I'm looking to deploy Ubuntu on Asus eepc netbooks within my school as the current xp home option is sadly lacking.

I have a number of problems that I need to overcome:

Force netbook to connect to wireless, pre-login - [COLOR=Blue]Done via the "Available to all users" option in NetworkManager.[/COLOR]

Join Ubuntu to domain for authentication - [COLOR=Blue]Done via installing & configuring likewise-open.[/COLOR]

Allow users to log in without prepending the domain (eg domianname\username), as users won't be able to cope with this - [COLOR=Red]Not done & assistance needed.[/COLOR]

Automatically mount the current users Windows network folder upon login. [COLOR=Red][COLOR=Black]The home folder could possibly be obtained by querying the Active Directory z:\ drive location. - [/COLOR][/COLOR][COLOR=Red]Not done & assistance needed[COLOR=Black].[/COLOR][/COLOR][COLOR=Red]

[/COLOR][B][I]I would appreciate assistance very much & I consider that introducing Linux to schools is a very important project.

I have to [/I]*work at introducing Ubuntu in a windows world. Please don't "help" by saying "Get rid of Windows".*[/B]

Many thanks,

Chris. :p

---

### Post by chrismyers on 2011-02-07
I think I found one fix myself for prepending the domain to ease the login for users.

I think I need to add:

winbind use default domain = yes

to either /etc/samba/smb.conf or maybe /etc/samba/lwiauthd.conf

I need to test.

I still need assistance with mounting Windows network home folders (My Documents).

---

### Post by m47h3us on 2011-02-16
> Allow users to log in without prepending the domain (eg domianname\username), as users won't be able to cope with this

You can use Likewise-open 6 which has the opinion to enable default user name prefix and enter your domain prefix in.

---

### Post by grahammechanical on 2011-02-16
I really do not know what I am talking about but I am thinking that you need some sort of script that you can list as a Startup Application. I assume that you would set up each machine to have an anybody type user account that does not have administrator privileges. And that this anybody user would have automatic login. At this point a script would run to set up the Windows Network folder. Is this the idea? If only I knew how to do it.

Regards. I wish you success.

I would like to see Canonical take as much interest in what you are doing as they did when they recently heard about a computer journal deciding to get its journalists to trial Ubuntu for a day. Canonical sent someone from HQ to help them overcome the installation problems. Helping you would help them get a look-in to install Ubuntu on school computers in England. Which would be a good idea in view of the spending cuts.

---

### Post by chrismyers on 2011-10-17
Cheers Matty for your assistance with prepending the domain - I know I didn't reply sooner, but as I know you personally this seemed a bit silly.
 
> **chrismyers said:**
> 
 
Automatically mount the current users Windows network folder upon login. [COLOR=red][COLOR=black]The home folder could possibly be obtained by querying the Active Directory z:\ drive location. - [/COLOR][/COLOR][COLOR=red]Not done & assistance needed[COLOR=black].[/COLOR][/COLOR]
 

 
I still need assistance with this one. Any takers?

---

