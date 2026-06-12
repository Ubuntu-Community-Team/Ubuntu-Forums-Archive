---
title: "Viewing previews in folders."
date: 2006-02-02
forum: Desktop Environments
---

### Post by YourSurrogateGod on 2006-02-02
I remember in Gnome that whenever I went to a folder full of pictures, it would start showing me previews of them (small ones.) How can I turn this on in KDE? I initially went to settings -> components -> file manager -> previews & meta-data and increased the max file size to 100MB.

Also, I have KDE 3.4.

---

### Post by mlomker on 2006-02-02
In 3.5 you can go under View, View Mode, Icon view.

---

### Post by Adrian on 2006-02-02
[QUOTE=YourSurrogateGod]I remember in Gnome that whenever I went to a folder full of pictures, it would start showing me previews of them (small ones.) How can I turn this on in KDE? I initially went to settings -> components -> file manager -> previews & meta-data and increased the max file size to 100MB.

Also, I have KDE 3.4.[/QUOTE]

Right now I'm using KDE 3.4.2b on SUSE.
When I launch Konqueror in file manager mode, I can enable previews in the *view->preview* menu. This menu will not exist in the text-based view modes, so make sure to use icon view (as mlomker said).

---

### Post by YourSurrogateGod on 2006-02-02
I did everything you guys told me, I still can't see the previews.

---

### Post by Jucato on 2006-02-02
Did you do these?

View > View Mode > Icon View; then

View > Preview > Make sure that "Images" is checked/activated

Just make sure that you are currently viewing files, not web pages, in Konqueror because the View Menu will change depending on what's on the current page.

---

### Post by YourSurrogateGod on 2006-02-03
[QUOTE=Fenyx]Did you do these?

View > View Mode > Icon View; then

View > Preview > Make sure that "Images" is checked/activated

Just make sure that you are currently viewing files, not web pages, in Konqueror because the View Menu will change depending on what's on the current page.[/QUOTE]
Yup, did all of that and no go. I went to a folder where I had a bunch of *.jpg files and didn't see a thing. Then I went to a folder that had videos, no go there either.

---

### Post by YourSurrogateGod on 2006-02-04
I take it's a bug if this isn't working? Or is there something else that I could have possibly messed up? I remember it worked at one point (right after I installed KDE), but it won't now for some reason.

---

### Post by mlomker on 2006-02-05
You could try reinstalling **konq-plugins**.  I did a search in Synaptic and it sounds related.

In my opinion something isn't a bug unless it doesn't work on a clean operating system install.  More than likely one of the dependent programs that handles that is missing or a file was deleted, etc.

---

### Post by YourSurrogateGod on 2006-02-05
[QUOTE=mlomker]You could try reinstalling **konq-plugins**.  I did a search in Synaptic and it sounds related.

In my opinion something isn't a bug unless it doesn't work on a clean operating system install.  More than likely one of the dependent programs that handles that is missing or a file was deleted, etc.[/QUOTE]
I guess it's a bug. It didn't work.

I have KDE 3.4 now. Maybe this type of problem will go away if I upgrade to 3.5 (just a hunch.) How can I upgrade to 3.5?

---

### Post by Jucato on 2006-02-05
This is for upgrading to KDE 3.5.1:
[http://kubuntu.org/announcements/kde-351.php]("http://kubuntu.org/announcements/kde-351.php")

This one is for KDE 3.5:
[http://kubuntu.org/announcements/kde-35.php]("http://kubuntu.org/announcements/kde-35.php")

It might or might not be a bug, but probably a setting or configuration that went wrong. Hopefully upgrading might solve it. if not, try to remember what you did before the previews stopped working (since you mentioned that it worked before).

---

### Post by YourSurrogateGod on 2006-02-05
[QUOTE=Fenyx]This is for upgrading to KDE 3.5.1:
[http://kubuntu.org/announcements/kde-351.php]("http://kubuntu.org/announcements/kde-351.php")

This one is for KDE 3.5:
[http://kubuntu.org/announcements/kde-35.php]("http://kubuntu.org/announcements/kde-35.php")[/quote]
Thanks.
[quote=Fenyx]It might or might not be a bug, but probably a setting or configuration that went wrong. Hopefully upgrading might solve it. if not, try to remember what you did before the previews stopped working (since you mentioned that it worked before).[/QUOTE]
I honestly don't remember.

---

### Post by YourSurrogateGod on 2006-02-05
I just upgraded, it didn't work.

One question though. If I upgrade, do I have to update my NVIDIA drivers again?

---

### Post by YourSurrogateGod on 2006-02-05
[QUOTE=Fenyx]It might or might not be a bug, but probably a setting or configuration that went wrong. Hopefully upgrading might solve it. if not, try to remember what you did before the previews stopped working (since you mentioned that it worked before).[/QUOTE]
I just fixed it.

Settings -> Configure Konqueror -> Previews & Meta Data
Go down the list of protocols and check mark the "local protocols" part.

You're right, it was something that I screwed up from the beginning.

---

### Post by Jucato on 2006-02-06
Glad you found your solution.
and no, you don't have to update your nvidia drivers. nvidia is related to the x server directly and is only indirectly related to the Desktop Environment (in this case, KDE). So modifying one doesn't mean you have to modify the other. Even if you modify x server itself, you don't have to reinstall KDE. Don't you just love how Linux separates these things to make life a bit easier? :D

---

### Post by YourSurrogateGod on 2006-02-06
[QUOTE=Fenyx]Glad you found your solution.
and no, you don't have to update your nvidia drivers. nvidia is related to the x server directly and is only indirectly related to the Desktop Environment (in this case, KDE). So modifying one doesn't mean you have to modify the other. Even if you modify x server itself, you don't have to reinstall KDE. Don't you just love how Linux separates these things to make life a bit easier? :D[/QUOTE]
Tru...

---

