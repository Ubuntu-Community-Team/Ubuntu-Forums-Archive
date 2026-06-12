---
title: "Permission denied to change brightness?"
date: 2009-01-11
forum: General Help
---

### Post by scathmandra on 2009-01-11
I am being very annoyed right now.

I've had a hell of a lot of problems with Hardy on my Inspiron 1501, especially with brightness. When I first installed, the FN shortcut for the brightness keys didn't work(FN up, FN down). I managed to fix this by using AaronMT's fix from [here]("http://www.ubuntu1501.com/2008/04/overview-of-ubuntu-804-hardy-heron-on.html"). 

And now it's failed on me again. But this time the problem seems to be different: I have tried to do the manual terminal fix, but get the following output. (The code itself shows me figuring I should go to root and being denied again.)
```
bernard@Nicodemus:~$ echo -n 62 > /proc/acpi/video/VGA/LCD/brightness
bash: /proc/acpi/video/VGA/LCD/brightness: Permission denied
bernard@Nicodemus:~$ sudo -s
[sudo] password for bernard: 
root@Nicodemus:~# echo -n 62 > /proc/apci/video/VGA/LCD/brightness
bash: /proc/apci/video/VGA/LCD/brightness: No such file or directory
root@Nicodemus:~# 

```

I can only assume that it doesn't work because I semi-recently changed over to Intrepid. I can't change the brightness at all now, and have no bloody idea what caused it because this computer's been plugged in all week, so ostensibly anything could have caused it.

Anyone else have this? Can anyone help me to solve it?

---

