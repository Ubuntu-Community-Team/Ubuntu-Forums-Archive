---
title: "accessing my debian machine with ubuntu with samba"
date: 2006-06-26
forum: Desktop Environments
---

### Post by degel3030 on 2006-06-26
is there anything different i need to do to the smb.conf in order to allow me to browse my debian server with ubuntu nautalis (i think thats what its called) i can see the workgroup but when i try and access it, it pops up with a middle finger and says 
The folder contents caould not be displayed.
Sorry, couldn't display all the contents of
"Windows Network: workgroup".

now all the stuff i read about is for windows to access linux (or the other way around) so is there something different i need to do?

---

### Post by Dubbayoo on 2006-06-26
Nothing different. Install samba on the debian box, configure some samba shares on it and go to town. I'm not sure why you wouldn't just nfs in this case. You could still browse with nautilus.

---

### Post by degel3030 on 2006-06-26
well incase i go crazy and boot up the ol winders machine, but i would like to get this going, still cant, i even pretty much copied [http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+windows](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+windows) and i still cant get it, do i have to configure something in ubuntu to be able to see the files?

---

