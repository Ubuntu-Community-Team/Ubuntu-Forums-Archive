---
title: "How to make subtitles?"
date: 2006-05-21
forum: Desktop Environments
---

### Post by hamil on 2006-05-21
Hello!

I have some avi files I would like to add some subtitles to.
I am looking for an application that can help me in that work. Prefer if it also is possible to synchronize the text to the picture at the same time.

Any good recomendations?

Thanks!

---

### Post by hamil on 2006-05-21
Well, downloaded ["subtitle editor"](http://kitone.free.fr/subtitleeditor/)
and did try to get it working... But not able to use it togheter with Mplayer, but it looks like it is a promising application..

Also found something called [Sabbu](http://www.sabbu.com/), but that one I have not even managed to compile on my machine, getting some GTK2 errors..

Will keep this post updated, and also looking forward to some inputs from other persons using a GUI for the making of subtitles..

---

### Post by precinto on 2006-08-18
Hi there. I don't know if you managed to solve it.

Right now you can easily install subtitleeditor from the repository on this web: [http://repository.debuntu.org/](http://repository.debuntu.org/)

It seems to work well for me. The only problem is that you cannot preview the subtitles within the program, which I find very important.

On the other hand, Sabbu can preview them. But I cannot compile it either. It asks if GTK+ is correctly installed and stops the configure script. The thing I don't know is if you can easily translate subs. By the way, Sabbu is no longer being developed. The developer says on the homepage that he'd be happy if someone would continue the work.

If you got to compile it I'd be grateful to know how. Meanwhile I'll still go back to Windows to use Subtitle Workshop and looking for some alternatives.

---

### Post by danielph on 2006-09-01
Have you tried ksubtile (that is not a typo) - it is in the repos. You can preview in MPlayer

---

### Post by noup on 2006-09-02
Hi,

You may also want to try [Gnome Subtitles]("http://gsubtitles.sourceforge.net"). It's still in its first version but might be worth a try. It (unfortunately) doesn't support movie previewing yet.

---

### Post by danielph on 2006-09-03
I thought I should mention that I have had some problems with character sets with French subtitles. Things like the é ç è à characters and others caused a problem. Take for example the second subtitle on the film motorcycle diaries. When I open it up in gedit I get this:
```
C'est un fragment de nos vies menées
parallèlement quelque temps...
``` 
which is correct.

But,  in ksubtile I get this:111
```
C'est un fragment de nos vies men&#65533;s
parall&#65533;ement quelque temps...
``` 
I haven't tried to run ksubtile in it's native enviroment, only under Gnome, but if anyone can shed some light on this ....

thanks

---

