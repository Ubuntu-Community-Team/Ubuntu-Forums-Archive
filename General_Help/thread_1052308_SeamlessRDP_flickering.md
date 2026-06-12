---
title: "SeamlessRDP flickering"
date: 2009-01-27
forum: General Help
---

### Post by james.king@4act.com on 2009-01-27
I have spent quite a bit of time getting seamlessrdp working on my Intrepid AMD64 box. However, I am stuck with one problem and google has turned up nothing on the issue. 

When I run my Photoshop CS3 or Illustrator CS3 through seamlessRDP the child windows of those apps (layers, colors,...) flicker very slowly as if they are constantly redrawing and taking a long time to do so. 

Anyone else run into a similar problem and have an idea of what to do?

Thanks

---

### Post by Ampersand. on 2009-02-11
Damn.

---

### Post by mchamplain on 2010-02-14
I didn't have that exact problem but if I use the -A option then everything is created in a window (sidebar, toolbar, menu) so I went with those options:

```

rdesktop -D -K -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Adobe\Adobe Photoshop CS4\photoshop.exe" 192.168.0.XXX:3389 -u USERNAME -p PASSWORD -a 16 -g 1680x963

```

that way photoshop is opened fullscreen and I change the height (963) to fit inside my top and bottom panel in Ubuntu.
That was the best result for me.

But for other applications (ie: notepad) I use -A instead of -D.

---

