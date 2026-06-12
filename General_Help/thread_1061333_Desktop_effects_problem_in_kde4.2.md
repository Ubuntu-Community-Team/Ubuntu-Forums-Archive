---
title: "Desktop effects problem in kde4.2"
date: 2009-02-05
forum: General Help
---

### Post by wackosimon on 2009-02-05
Hi, I a week ago i installed the new KDE 4.2 on kubuntu 8.10. All was fine until yesterday. I cannot get the desktop effects to load. the message i get says:

Failed to activate desktop effects using the given configuration options. Settings will be reverted to their previous values.
Check your X configuration. You may also consider changing advanced options, especially changing the compositing type.

I have reinstalled various drivers recommended by others but still no luck.
glxinfo comes up with:

name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10


I hope you guys can help, its driving me crazy.
Thank you in advance.

Simon

---

### Post by fatbuttlarry on 2009-04-14
Simon,

I'm having this same problem after installing 9.04 Jaunty and applying updates.

[GLX gears still runs 10,000fps]("http://georgia.ubuntuforums.org/attachment.php?attachmentid=109838&stc=1&d=1239758634"), Neverball (in the repo's) works great and so do my Steam games (Half-Life 1 using OpenGL, etc).

Not sure what's causing this.  The [SuSE forums]("forums.opensuse.org/applications/395101-failed-activate-desktop-effects-using-given-configu.html") have some people complaining about it as well, but the provided command is not part of the standard Kubuntu install. Any help is appreciated!

This is especially disappointing as the features worked great before updates were applied.  Cheers.

-Tres

---

### Post by abn91c on 2009-04-14
on the desktop effects screen click on the advanced tab, change composting type to Xrender

---

### Post by fatbuttlarry on 2009-04-14
> **abn91c said:**
> on the desktop effects screen click on the advanced tab, change composting type to Xrender

abn91c,

Thanks for the quick reply.  The SuSE forums suggested that as well.  No dice on my end.

I'd guess OpenGL would be preferred. As you can see from [this screenshot]("http://georgia.ubuntuforums.org/attachment.php?attachmentid=109838&stc=1&d=1239758634"), OpenGL is working well.  There's a couple updates waiting... let me apply those too and reboot.  The Xrender doesn't even seem to stick so I'm not entirely convinced the option is taking.

-Tres

---

### Post by fatbuttlarry on 2009-04-14
Applied the 36 Jaunty updates and rebooted.  Went back into System Settings -->  Desktop --> Desktop Effects --> General.  I rechecked "enable desktop effects" and [compositioning is working again]("http://georgia.ubuntuforums.org/attachment.php?attachmentid=109842&d=1239759750") now in OpenGL mode.

Don't know if the reboot had anything to do with it, but happy to see them working.

Cheers!

:popcorn:

-Tres

---

