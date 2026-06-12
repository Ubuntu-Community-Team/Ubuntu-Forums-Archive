---
title: "VPN - refuse-eap key for gconf-editor"
date: 2009-03-06
forum: General Help
---

### Post by www.Emucraze.com on 2009-03-06
Hi all!

My university offers wireless Internet which requires the use of a VPN to access it.

Now I am running Ubuntu 8.10 and as far as I understand the setting "refuse-eap" needed to be enabled in the advanced settings and due to a bug, this setting is absent.

I learned later, that you can manually add this setting in by opening the Terminal and then "gconf-editor"

In that... I opened...

[B]terminal > gconf-editor

System > Networking > Connections > Either (folder, 1, 2, 3, 4, etc) > vpn[/B]

[COLOR="Lime"]New Key[/COLOR]

Name: **refuse-eap**

Type: **String**

Value: **Yes**

Click OK

Done!

That was all good and all, but unfortunately, this setting must be placed in for every restart because it is not saved :(

Is there a way I can save it (I am a noob @ linux) so that **_I don't have to keep re-adding this key every time I boot into ubuntu_**?





cheers!:guitar:

---

### Post by www.Emucraze.com on 2009-03-07
Is there not **one** person that knows the answer to this? or axplain what can or cannot be done? ](*,)

---

