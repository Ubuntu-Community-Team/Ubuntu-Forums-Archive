---
title: "Running multiple X servers."
date: 2009-04-05
forum: General Help
---

### Post by jwbrase on 2009-04-05
I've been trying to get a second instance of X running on one of the virtual consoles, and have not been having good success.

I found this thread: [http://ubuntuforums.org/showthread.php?t=213756](http://ubuntuforums.org/showthread.php?t=213756)

but the method suggested there: ```
$ startx -display :1 -- :1 vt8 &
```, in addition to the fact that it seems to be missing a sudo, doesn't seem to do anything on tty8 or higher (hitting ctrl-alt-FN to go to the virtual terminal takes you to a blank screen with a text cursor at the top, with no evidence of x actually running), and leads to the computer going to a black screen and locking up for tty6 or lower, neccesitating a restart. (He mentions some potential problems one might encounter, but none of them seem to be the one I'm having). Also, the thread is almost three years old, so the information in it might be outdated.

---

