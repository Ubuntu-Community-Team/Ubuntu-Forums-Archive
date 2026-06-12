---
title: "X11 font server support on modern Xorg X-server"
date: 2023-05-17
forum: Desktop Environments
---

### Post by reinier85 on 2023-05-17
Dear community,


I am currently supporting an extremely old application with a GUI directly written with Xlib.

Originally, this application executed on a very old Linux distribution and now the goal is to migrate it to Ubuntu.

One of the many challenges that I am facing is to still support the ancient IBM Type1 Courier font.

The application serves many X-terminals across a network and currently the font is provided by a XFS font server.

The problem I am currently having, is that for some reason I am not able to register the font server with the remote X-servers (terminals).

I could not find the various xfs packages from the repositories, so I build them from source from the FreeDesktop Gitlab repositories:

[https://gitlab.freedesktop.org/xorg](https://gitlab.freedesktop.org/xorg)

I can confirm that the **xfs** server is running by using the **xfsinfo **and **fslsfonts** utilities.

Then I try to set the font server using xset, e.g.

> xset fp+ tcp/localhost:7100

But no matter what I do, I keep on getting this error message:


> xset:  bad font path element (#7), possible causes are:
    Directory does not exist or has wrong permissions
    Directory missing fonts.dir
    Incorrect font server address or syntax

I have read up a bit on this and it seems that newer Xorg X-servers might not even support xfs font servers anymore. Is this perhaps indeed the case?

An alternative is to rather use the more "modern" approach of client-side rendering using fontconfig / libXft, but because this is such an old application, I only want to go this route if I must.

Can you guys please advise?

Many thanks in advance!

Best regards

---

