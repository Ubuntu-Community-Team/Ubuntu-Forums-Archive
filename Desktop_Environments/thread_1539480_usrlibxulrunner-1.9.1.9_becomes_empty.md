---
title: "/usr/lib/xulrunner-1.9.1.9 becomes empty"
date: 2010-07-26
forum: Desktop Environments
---

### Post by nobani on 2010-07-26
Hi all,
when I open a terminal from any where I get the following massage:
```
ERROR: ld.so: object '/usr/lib/xulrunner-1.9.1.9/libmozjs.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/xulrunner-1.9.1.9/libmozjs.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/xulrunner-1.9.1.9/libmozjs.so' from LD_PRELOAD cannot be preloaded: ignored.

```these massages were appear after I installed the FREEWRL (3D visulaization ) program.
I added the following two lines in the .bashrc :
```
export G4VRMLFILE_VIEWER=freewrl
export LD_PRELOAD=/usr/lib/xulrunner-1.9.1.9/libmozjs.so freewrl
```also I do the following command in the terminal:
```
sudo cp /usr/share/fonts/truetype/VeraMono.ttf /usr/share/fonts
```other problem that when I did that , it was a some files and folders inside /usr/lib/xulrunner-1.9.1.9 but now its empty and the application does not work ( it was work)
there was no /usr/lib/xulrunner-1.9.1.10 but now its appear!!!!
I changed the second line to be :
  ```
export LD_PRELOAD=/usr/lib/xulrunner-1.9.1.10/libmozjs.so freewrl
```but the first massage is still appears and the application worked for a few seconds only.

I am using openSUSE11.2 (i586) with KDE4.3.5

I will be appreciated for any help or any idea  :)

respectfully,

---

