---
title: "small problem"
date: 2009-05-02
forum: General Help
---

### Post by rudi009 on 2009-05-02
a few hours back i installed mac4lin theme on my ubuntu 9.04 and it shifted the window icons-close, max,min to the left.now in all the themes its on the left.i want to shift them back to right.help!!

---

### Post by rob1408 on 2009-05-02
Press 'alt' and F2. Run gconf-editor.  Select 'Apps', Select 'Metacity', Select 'General' and it's the eighth option down.  You just have to reverse what is already there.

---

### Post by rudi009 on 2009-05-02
problem solved and it was fun..can you please give some link to read about all this stuff and play.

---

### Post by rudi009 on 2009-05-02
also I am not able to replace the icons with the ones i downloaded- coz the permission is denied in the system directories.what should i do? thanks..

---

### Post by rob1408 on 2009-05-02
I only found the solution by trawling through google after having the same problem.  I installed mac4lin through the shellscript and it installed the icons automatically.  You can try solving permission problems by using Nautilus (sudo Nautilus), this opens a file browser with root permission enabling you to move stuff around.

---

