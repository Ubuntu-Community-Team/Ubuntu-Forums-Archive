---
title: "New Users and Sound"
date: 2005-07-14
forum: Desktop Environments
---

### Post by zerhacke on 2005-07-14
I'm new to Linux in general so please don't attack me for not knowing.

I have a Ubuntu 5.04 setup.  I had for a while now just one user.  I have set the root password to something other than default.

I added a new user for my stepson the other day.  It works, but it cannot use any audio.  I checked the "use audio" tab when I created his account.  For some reason he still cannot hear any sounds.  I have XINE compiled from source, both lib and ui, I have removed Totem entirely, and I have XMMS.

On my account I can use either XMMS or XINE with no problems other than occasionally XINE does not want to close (I have to kill it via commandline).  On his account he cannot hear any sounds period.

Does anyone know how to fix this?

---

### Post by badrinarayan on 2005-07-14
Go to **System > Administration > Users and Groups**
Select his account, click on Properties.

Make sure the following are checked:

[list]
[*]Use Audio Devices
[*]Use Video Acceleration
[/list] 

Also see [http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly) and [http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

Regards
Badri

---

### Post by zerhacke on 2005-07-14
[QUOTE=badrinarayan]Go to **System > Administration > Users and Groups**
Select his account, click on Properties.

Make sure the following are checked:

Use Audio Devices
Use Video Acceleration

Also see [http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly) and [http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

Regards
Badri[/QUOTE]
Both of those are already checked.  Sound works perfectly on my login so I know sound is configured correctly.  It just does not work on his login.

---

### Post by badrinarayan on 2005-07-14
Can you run xmms or xine from command line in his login and post the audio related error. Did you try changing the Audio Input Plugins in XMMS for him to ESD?

Regards
Badri

---

### Post by zerhacke on 2005-07-14
Changing his Audio Output plugin to ESD fixed the problem.  Thank you very much.

---

