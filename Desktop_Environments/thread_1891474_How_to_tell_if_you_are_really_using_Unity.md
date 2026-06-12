---
title: "How to tell if you are really using Unity"
date: 2011-12-05
forum: Desktop Environments
---

### Post by ratcheer on 2011-12-05
I see a lot of complaints here and elsewhere on the 'net that people say they select the Ubuntu login and it succeeds, but that they are going into Unity 2D, instead.

My question is, how do you tell the difference?

I can log in to both regular Ubuntu and Unity 2D. Honestly, they look the same to me. Is there supposed to be a dramatic difference. I am pretty sure my system is configured to use 3D. E.g., running glxgears shows a very nice 3D effect. But how do I know for sure if, when I am running Unity, it is really the 3D version?

Thanks,
Tim

---

### Post by 3Miro on 2011-12-05
Unity 2D and 3D are deliberately made similar. Probably the best way to test it visually is to try the Workspace zoom-out effect, they look slightly different.

You can install CompizConfig-Settings-Manager, this is a settings program that vies you plenty of adjustment for compiz and Unity. From CCSM go into the Unity plugin and change the size of the icon launchers, Unity 3D will respond to CCSM, Unity 2D will not.

PS: Another way is to start Gnome-system monitor and look into the running processes and search for compiz. Unity 3D uses Compiz, Unity 2D does not.

---

### Post by ratcheer on 2011-12-05
Excellent. I have compiz running, so it must be Unity 3D. Thank you!

Tim

---

