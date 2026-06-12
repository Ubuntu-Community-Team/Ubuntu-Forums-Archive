---
title: "replacing and or moving files??"
date: 2008-12-18
forum: General Help
---

### Post by rixtr66 on 2008-12-18
Im trying to copy files from my home folder to my Blender folder.
I recently had to reinstall ubuntu after crashing it(i seem to be good at crashing linux systems):redface:anyway imanaged to save my python scripts and other files,I used nautilus to copy the files and paste them into the blender folder,but they only had root permission,so i did the share option and i got access but blender can only access a small portion of the scripts?
how do i copy these files and have full access?
help would be greatly appreciated!!!
Rick :-k

---

### Post by lovelyvik293 on 2008-12-18
By using the chmod and the chown,you can change the permissions of that folder or file.

---

### Post by pietjanjaap on 2008-12-18
gksudo nautilus

Now you can do wat you want. Make a icon if needed.
Watch out this is unsafe.

Start the live cd then you can do also everything.

---

### Post by rixtr66 on 2008-12-18
ok ive used nautilus,and discovered how to change permissions,by using the options menu in nautilus.but as it turns out i can copy files to .blender
without nautilus?but blender in /usr/share/blender i have to use nautilus?
now im confused!wich blender file should i use to add texture files and renders etc.??
Rick

---

### Post by oldos2er on 2008-12-18
No, you don't have to use Nautilus. Anytime you're working outside your home directory, you need root privileges. You can do this in the terminal by prepending "sudo" to the cp command.

---

### Post by vanadium on 2008-12-18
As soon as you are not allowed to copy files, you should think twice. There is a good reason why normally you shouldn't copy there. If you know what you are doing, then indeed you use root permissions to work in "restricted areas".

.blender is a hidden user folder that is private to you only. Any changes will affect only you. You willhave all rights as a user there. /usr/share/blender is a global system folder. Any changes there will affect all users. That is why root is the only one that should write there.

Youre best bet is trying to manipulate .blender in order to achieve what you want.

---

### Post by rixtr66 on 2008-12-18
@vanadium;Thanks!i thought that might be the case.Thanks for explaining it to me!!!wasnt too sure though.
Rick  :guitar:

---

