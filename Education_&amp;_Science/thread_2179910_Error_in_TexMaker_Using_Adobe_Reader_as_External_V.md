---
title: "Error in TexMaker Using Adobe Reader as External Viewer in Precise"
date: 2013-10-10
forum: Education &amp; Science
---

### Post by jrolland2 on 2013-10-10
Hello, all!

I am running Ubuntu 12.04 Precise Pangolin LTS with TexMaker 3.2

I am trying to use Adobe Reader as the "Pdf Viewer" -> "External Viewer" option with 

```

acroread %.pdf

```

as the command, but I keep getting the error message

```
 Gtk-Message: Failed to load module "atk-bridge"


```

twice before the document is successfully displayed in Adobe Reader.

I'd just like to make sure there isn't any more serious issue.

Is there some better command, or maybe some options of the above command, that will allow me to avoid the 

```
 Gtk-Message: Failed to load module "atk-bridge"


```

error messages, and perhaps some more serious errors down the road?

Thanks much in advance for any assistance you can provide.

---

### Post by entropy1 on 2013-10-10
I just installed texmaker 3.2 in 12.04, and it works for me.  Try re-installing texmaker.  If that doesn't help, try re-installing acroread.  Otherwise, maybe someone else can post a better answer.

---

### Post by Buntu Bunny on 2013-10-16
Welcome to the forums, jrolland2. 

I got a similar message when trying to open Adobe Reader with the command you used. Ditto with simply

```
acroread
```

However, it opened. I've been using Reader quite a bit lately, but always open in from the application menu; no error message then. What happens when you open it via a menu or launcher icon?

I searched about for "atk-bridge', and apparently others have had the same error message for different applications and with different distros. Unfortunately, no one received a helpful reply.

Adobe support for the Linux version of Reader isn't all that great. Do you really need Adobe Reader, or would one of the more Linux friendly pdf readers do?

---

