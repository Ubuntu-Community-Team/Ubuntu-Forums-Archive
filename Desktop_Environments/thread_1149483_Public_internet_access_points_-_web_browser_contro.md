---
title: "Public internet access points - web browser control"
date: 2009-05-05
forum: Desktop Environments
---

### Post by kunix on 2009-05-05
Hi,

I'm currently building a Linux-based PIAP environment for my university.
 
I know that there are some existing projects on SF but I have some particular requirements to meet and building the system from scratch is just more of a educational benefit for me.

I have most issues covered but one is still keeping me awake at night ;)

The main application available is of course the web browser. 
The system logs in automatically and I want the browser to:
[LIST]
[*]start with the xsession
[*]restart when user manages to close it.
[/LIST]

The first part is trivial but I need help in writing a script that could control the browser restarting part.

I know of the files .xsession and .xinitrc in the home directory but my Ubuntu 8.04.2 platform seems not to include them in the login process 

For the used window manager I'm considering Gnome, IceWM and Fluxbox with the preference of IceWM - all of them in their base installations. 

Hope that someone will be able to help.

---

