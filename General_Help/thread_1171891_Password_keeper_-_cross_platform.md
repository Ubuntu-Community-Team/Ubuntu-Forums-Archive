---
title: "Password keeper - cross platform"
date: 2009-05-27
forum: General Help
---

### Post by celem on 2009-05-27
FYI: 
I know that the Palm Pilot isn't so popular anymore but I love mine and use it every day. I use Keyring for Palm OS on my Palm to securely keep all passwords, etc. I also use both an Xp machine and a Ubuntu Jaunty machine. Wanting a cross-platform soultion that will work in all three environments, the best solution that I have found is Palm OS on my Palm and the java based KeyringEditor on each of the desktops. I can edit/display the password database in all three environments.

I recommend using the java based KeyringEditor as modified by Peter Reutemann. Make sure that you use the "-all-records" command line argument, i.e.,:
java -jar keyringeditor.jar -all-records /folderwithDb/Keys-Gtkr.PDB. See:
[http://tinyurl.com/r7jels](http://tinyurl.com/r7jels)

The Keyring for Palm OS is at:
[http://gnukeyring.sourceforge.net/](http://gnukeyring.sourceforge.net/)

There is no conduit for either the XP or Ubuntu but there are workarounds that work well.

---

