---
title: "Problems with Edgy and Player/Stage/Gazebo"
date: 2007-03-04
forum: Education &amp; Science
---

### Post by uncolorcoordinated on 2007-03-04
I just finished what I thought was a successful build of Player/Stage/Gazebo, but I'm getting a couple of errors when I try to run a world that have me stumped.

The first error has to do with the display drivers. This is my output when I try to run example.world:
```
starting server
waiting for server
** Gazebo 0.8.0 **
* Part of the Player/Stage Project [http://playerstage.sourceforge.net].
* Copyright 2000-2005 Brian Gerkey, Richard Vaughan, Andrew Howard,
* Nate Koenig and contributors.
* Released under the GNU General Public License.
using display [:0.0]
libGL warning: 3D driver claims to not support visual 0x4b
X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  21
  Current serial number in output stream:  22
server died
stopping server
```

Now, when I change then render method in the .world file to XLIB, I get this:
```
starting server
waiting for server
** Gazebo 0.8.0 **
* Part of the Player/Stage Project [http://playerstage.sourceforge.net].
* Copyright 2000-2005 Brian Gerkey, Richard Vaughan, Andrew Howard,
* Nate Koenig and contributors.
* Released under the GNU General Public License.
using display [:0.0]
libGL warning: 3D driver claims to not support visual 0x4b
rendering: [Xlib unmapped] direct [yes] RGBA [8 8 8 8] depth [24]

ODE INTERNAL ERROR 2: The centre of mass must be at the origin. in dBodySetMass()
server died
stopping server
```

The display error I can kind of get around, but the ODE error has me stumped...

Some specs:
CPU:     Intel(R) Celeron(R) CPU 1.70GHz
Display: Intel(R) 82845G
OS:      Ubuntu 6.10 
Kernel:  2.6.17-10-generic

Thanks!

---

### Post by frenque on 2007-04-10
I'm having exactly the same issue with a ATI Radeon Mobility M6.
this is not a gazebo bug, but a failure of the xorg radeon driver. Too bad the ATI closedsource driver doesn't have any support for the Mobility M6 ...

hope to see a fix, i have no clue how to resolve this.

---

### Post by slaanco on 2007-04-11
I'm not sure if it will be of any help, but have u tried to install your drivers through envy ?

```

wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb

```

---

### Post by Princegiri on 2007-12-04
[http://ubuntuforums.org/showthread.php?p=3889012#post3889012](http://ubuntuforums.org/showthread.php?p=3889012#post3889012)

This is a thread to a problem that i have playerstage.... im pasting this link here because its tough to find playerstage users in the forums....  pls help me out.

---

