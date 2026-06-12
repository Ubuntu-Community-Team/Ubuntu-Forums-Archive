---
title: "Remove global menu bar from *Firefox* (22.0)"
date: 2013-06-28
forum: Desktop Environments
---

### Post by Newbunto on 2013-06-28
Yesterday all was working fine. Firefox *did not* use the global menu bar and selected other applications *did* e.g. Nautilus.

This morning suddenly Firefox started using the global menu bar. Nothing that I have done so far has fixed that, although with [FONT=courier new]apt-get autoremove ...[/FONT] (as discussed elsewhere in this forum) other applications are now *not* using the global menu bar. So right now Firefox is the only application using it and yet the main one that I don't want to be using it.

I think that this morning FireFox was updated via Update Manager (automatically offered and I accepted).

I've rebooted several times.

Suggestions?

---

### Post by dino99 on 2013-06-28
[http://www.google.fr/#tbs=qdr:y&sclient=psy-ab&q=ubuntu+global+menu+remove&oq=ubuntu+global+menu+remove&gs_l=hp.3..0i30j0i8i30l3.106220.116992.6.117312.25.18.0.7.7.0.66.925.18.18.0...0.0...1c.1.18.psy-ab.4oPiVhQT3_4&pbx=1&bav=on.2,or.r_qf.&bvm=bv.48572450,d.d2k&fp=c6186e8a239b59e&biw=1674&bih=925](http://www.google.fr/#tbs=qdr:y&sclient=psy-ab&q=ubuntu+global+menu+remove&oq=ubuntu+global+menu+remove&gs_l=hp.3..0i30j0i8i30l3.106220.116992.6.117312.25.18.0.7.7.0.66.925.18.18.0...0.0...1c.1.18.psy-ab.4oPiVhQT3_4&pbx=1&bav=on.2,or.r_qf.&bvm=bv.48572450,d.d2k&fp=c6186e8a239b59e&biw=1674&bih=925)

---

### Post by kennerc on 2013-06-28
Never mind what I said earlier... Didn't saw that you was using version 22.
Type in about:config and change the value of the line ui.use_unity_menubar to false.

---

### Post by Newbunto on 2013-07-05
Excellent, thanks. That did the trick.

---

