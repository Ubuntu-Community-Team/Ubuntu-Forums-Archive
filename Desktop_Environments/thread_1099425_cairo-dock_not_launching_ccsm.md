---
title: "cairo-dock not launching ccsm"
date: 2009-03-18
forum: Desktop Environments
---

### Post by Mineral on 2009-03-18
Hey all,

I have an issue where I cannot launch ccsm from my cairo-dock. I do have ccsm installed, and it opens from terminal and the system menus fine. I have also tried googling, but didn't get any helpful results.

Thanks for any help,
Kohei.

---

### Post by fabounet on 2009-03-18
any messages in the terminal, with cairo-dock -l debug ?

---

### Post by Mineral on 2009-03-18
```
message :  message :  (cairo-dock-animations.c:cairo_dock_start_animation:438)  
  cairo_dock_start_animation (Advanced Desktop Effects Settings, 0)
(applet-gvfs.c:vfs_backend_launch_uri:776)  
  vfs_backend_launch_uri (ccsm)
warning :  (applet-gvfs.c:_cd_find_target_uri:763)  
  Attention : Operation not supported
GConf Error: Bad key or directory name: "/desktop/gnome/url-handlers/": Key/directory may not end with a slash '/'
warning :  (applet-gvfs.c:vfs_backend_launch_uri:786)  
  gnome_integration : couldn't launch 'ccsm' [Operation not supported]
```

---

### Post by fabounet on 2009-03-18
it considers this launcher as a file
how did you make this launcher ?
I suggest to drop this one out of the dock, and drag the ccsm launcher from the Application Menu.

---

### Post by Mineral on 2009-03-19
Thanks, that fixed it.

I didn't actually create it, it was in one of the cairo-dock themes.

---

### Post by fabounet on 2009-03-19
ok, good to know
themes will be repackaged with the coming v2 anyway

---

### Post by Scubdup on 2009-03-19
Can anyone please tell me where can I find info on version 2?

---

### Post by fabounet on 2009-03-20
right-click on your dock -> Cairo-dock -> dev site ;-)
but it's a beta version.

---

### Post by Favux on 2009-03-20
Hi fabounet,

When I tried the right click on the dock to go to the developement site I got:
> **[SIZE="3"]Secure Connection Failed[/SIZE]**
   

An error occurred during a connection to developer.berlios.de.

You have received an invalid certificate.  Please contact the server administrator or email correspondent and give them the following information:

Your certificate contains the same serial number as another certificate issued by the certificate authority.  Please get a new certificate containing a unique serial number.

(Error code: sec_error_reused_issuer_and_serial)
        

The page you are trying to view can not be shown because the authenticity of the received data could not be verified.

    * Please contact the web site owners to inform them of this problem.

 
      
Thought you should know.

---

