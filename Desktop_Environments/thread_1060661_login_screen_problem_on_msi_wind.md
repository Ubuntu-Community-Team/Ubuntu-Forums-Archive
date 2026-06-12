---
title: "login screen problem on msi wind"
date: 2009-02-05
forum: Desktop Environments
---

### Post by jepong on 2009-02-05
good day... i did try kubuntu on a msi wind U100. but the login screen is not maximized to cover the whole 10.1 inch of the screen. it left garbage on it sides (left and right).

is there a way to maximize the logon screen? thanks.

---

### Post by jepong on 2009-02-22
attached is a photo of my msi wind and my problem.

---

### Post by jepong on 2009-03-12
this is a bug and here is the workaround

> 
--- /usr/share/kde4/apps/kdm/themes/oxygen/oxygen.xml 2008-10-04 12:44:53.000000000 +0200
+++  /usr/share/kde4/apps/kdm/themes/oxygen/oxygen.xml  2008-10-04 12:45:56.000000000 +0200
@@ -23,7 +23,7 @@
               text-color="#000000" disabled-text-color="#808080"/>
        <item type="svg" id="background" background="true">
               <normal file="background.svg"/>
-              <pos anchor="c" x="50%" y="50%" width="scale" height="100%"/>
+              <pos anchor="c" x="50%" y="50%" width="100%" height="scale"/>
        </item>
 
        <item type="rect" id="greeter">
 



---

### Post by Zorael on 2009-03-14
I suggest you make it 100%/100% to match the welcome screen (where icons pop up as it loads different aspects of the environment).

```
<pos anchor="c" x="50%" y="50%" width="**100%**" height="**100%**"/>
```

---

