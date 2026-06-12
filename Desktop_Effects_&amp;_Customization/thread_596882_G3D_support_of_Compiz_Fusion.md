---
title: "G3D support of Compiz Fusion"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by yookoala on 2007-10-30
Right now, the entire Compiz Fusion is built on [OpenGL](http://www.google.com.hk/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.opengl.org%2F&ei=I74mR8bzGoKWswLRq7Vw&usg=AFQjCNHwltCKoxAw9Z58OdYvKMLCq-we8A&sig2=IuzIdNUt3Qpcfw6TXd0tZg). Since [OpenGL](http://www.google.com.hk/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.opengl.org%2F&ei=I74mR8bzGoKWswLRq7Vw&usg=AFQjCNHwltCKoxAw9Z58OdYvKMLCq-we8A&sig2=IuzIdNUt3Qpcfw6TXd0tZg) only works on limited hardware, we cannot have desktop effect on majority of machines out there.

However, another 3D library, the [G3D cpp library](http://g3d-cpp.sourceforge.net/), works even if you don't have a 3D acceleration card. I think its a good idea to provide [G3D](http://g3d-cpp.sourceforge.net/) support when [OpenGL](http://www.google.com.hk/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.opengl.org%2F&ei=I74mR8bzGoKWswLRq7Vw&usg=AFQjCNHwltCKoxAw9Z58OdYvKMLCq-we8A&sig2=IuzIdNUt3Qpcfw6TXd0tZg) compatible hardware is not present. It may provide less desktop effect than [OpenGL](http://www.google.com.hk/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.opengl.org%2F&ei=I74mR8bzGoKWswLRq7Vw&usg=AFQjCNHwltCKoxAw9Z58OdYvKMLCq-we8A&sig2=IuzIdNUt3Qpcfw6TXd0tZg), but at least it con provide some to most computer. Plus one can think less about hardware compatibility when buying a machine for Ubuntu.

Right now, Windows Vista desktop effect only works on limited hardware. One can't really enjoy it on older PCs. On the other hand, Mac OS can provide good desktop effect even for older Mac machine (like PowerPC G3). I believe Ubuntu, like Mac OS, can provide beautiful and productive desktop effects to older PCs. And by doing that, Ubuntu can gain the user base from Windows XP users. What's better if you can get a better desktop without upgrading hardware and paying "the Windows tax"?

This is the best way I can think of to fix [Bug #1](http://www.google.com.hk/url?sa=t&ct=res&cd=1&url=https%3A%2F%2Flaunchpad.net%2Fbugs%2F1&ei=mb0mR8OVEZXusgLms_SBAQ&usg=AFQjCNFQolImMI1RWGpHfVj2LCP4PaGOoQ&sig2=9Y-RWLXZWgUgjPHg5TAPqA) for all Linux distributions. Do you agree?

I posted [a post on Compiz-Fusion forum](http://forum.compiz-fusion.org/showthread.php?goto=newpost&t=5109) days ago. It doesn't seems to gain attention from developers or users. If you guys agree with me, please say something there. Or you may tell the developers of Compiz Fusion by any means.

---

### Post by yookoala on 2008-01-07
For your interest. This is the architecture of g3d 
[IMG]http://g3d-cpp.sourceforge.net/html/3dengine.jpg[/IMG]

It is like Direct X on Windows.
If there is 3D graphic card on the computer, it redirect to OpenGL.
If there is no 3D graphic card on the computer, it runs on CPU.

If g3d is used as the base of Compiz Fusion, some desktop effect
could work on legacy PC at a reasonable speed.

---

