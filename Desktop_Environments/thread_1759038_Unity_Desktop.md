---
title: "Unity Desktop"
date: 2011-05-15
forum: Desktop Environments
---

### Post by macmike on 2011-05-15
I installed Ubuntu Server 11.04 with the Desktop environment. I was hoping to see and use the new look. When finished after a day of updating I am still on the Gnome desktop. How do I setup to use the new look I think it might be called Unity. I have dinked around all over and can see where to make the change. Any help appreciated.

macmike.

---

### Post by ivanovnegro on 2011-05-15
So you installed the newest version of Ubuntu.
Maybe your hardware does not support Unity?
You have to assure that your graphics card support 3D acceleration.

---

### Post by sikander3786 on 2011-05-15
> I installed Ubuntu Server 11.04 with the Desktop environment

Which DE did you install? For Unity, you might need to execute this command.

```
sudo apt-get install unity
```

Then from the GDM Login Screen under Sessions menu, choose 'Ubuntu' and login.

You'll see Unity only if your graphics card supports it as mentioned above ;-)

---

### Post by macmike on 2011-05-15
> **sikander3786 said:**
> Which DE did you install? For Unity, you might need to execute this command.

```
sudo apt-get install unity
```Then from the GDM Login Screen under Sessions menu, choose 'Ubuntu' and login.

You'll see Unity only if your graphics card supports it as mentioned above ;-)

When I do apt-get unity I get a message Unity is already the newest version. I think the DE is Gnome.

---

### Post by sikander3786 on 2011-05-15
Unity is also based on Gnome. If you logout and click your username at the Login Screen, what options have you got under 'Sessions'? Is 'Ubuntu' listed there?

---

### Post by garvinrick4 on 2011-05-15
Test for 3d unity support

```
/usr/lib/nux/unity_support_test -p
```

---

### Post by sanguinemoon on 2011-05-15
You probably just need to update your graphics driver :) I wouldn't be upset about not seeing Unity, though. I just installed it a couple hours ago and it's annoying  me.

---

### Post by macmike on 2011-05-16
> **garvinrick4 said:**
> Test for 3d unity support

```
/usr/lib/nux/unity_support_test -p
```

Here is the Results I get:

OpenGL vendor string; Nouveau
OpenGL renderer string: Mesa DRI nv11 20091015 x86/MMX/SSE2
OpenGL version string: 1.2 Mesa 7.10.2

Not software rendered: Yes
Not blacklisted: Yes
GLX fbconfig: Yes
GLX texture from pixmap: yes
GL npot or rect textures: Yes
GL vertex program: no
GL fragment program: no
GL vertex buffer object: Yes
GL framebuffer object: Yes
GL version is 1.4+ no

Unity supported: no

So I guess that answers the question! I have a Dell I might try it on and see if it will support Unity.

macmike

---

### Post by Krytarik on 2011-05-17
If you haven't done so already, go to "System -> Administration -> Additional Drivers" and try either installing the proprietary "nvidia" driver or the "experimental" one (3D-capable version of the "nouveau" driver).

Greetings.

---

### Post by NormanFLinux on 2011-05-17
I get that same info except GL 1.4+ is present on my HP Mininote 2133. No fear - the compositing engine can support Unity 2D just fine :)


OpenGL vendor string; Nouveau
OpenGL renderer string: Mesa DRI nv11 20091015 x86/MMX/SSE2
OpenGL version string: 1.2 Mesa 7.10.2

Not software rendered: Yes
Not blacklisted: Yes
GLX fbconfig: Yes
GLX texture from pixmap: yes
GL npot or rect textures: Yes
GL vertex program: no
GL fragment program: no
GL vertex buffer object: Yes
GL framebuffer object: Yes
GL version is 1.4+ no

Unity supported: no

---

### Post by macmike on 2011-05-17
> **Krytarik said:**
> If you haven't done so already, go to "System -> Administration -> Additional Drivers" and try either installing the proprietary "nvidia" driver or the "experimental" one (3D-capable version of the "nouveau" driver).

Greetings.

When I do that a message comes back that says No Proprietary Drivers are in use on this system.

---

### Post by Krytarik on 2011-05-17
> **macmike said:**
> When I do that a message comes back that says No Proprietary Drivers are in use on this system.
Ok. How about following my suggestion then!?

---

