---
title: "How-To COMPLETELY Remove C-F, Beryl etc"
date: 2007-09-01
forum: Desktop Effects &amp; Customization
---

### Post by The Pinny Parlour on 2007-09-01
How does one completely remove all the eye candy?  It's buggy as hell and just doesn't work well.

Thank you.

---

### Post by Inxsible on 2007-09-01
> **The Pinny Parlour said:**
> How does one completely remove all the eye candy?  It's buggy as hell and just doesn't work well.

Thank you.

Here's how you remove Compiz Fusion completely

[Remove Compiz Fusion]("http://ubuntuforums.org/showthread.php?t=533201")

---

### Post by The Pinny Parlour on 2007-09-01
Thank you.  Will give it a try.

---

### Post by The Pinny Parlour on 2007-09-01
Failed miserably.  Can anyone show me how to COMPLETELY rid my system of anything Compiz-Fusion/Beryl/Compiz related.  PLEASEEEEEEEEEEEEE.

---

### Post by Inxsible on 2007-09-01
> **The Pinny Parlour said:**
> Failed miserably.What failed ?? What errors did you get ?

You gotta give us more information than just "failed"

---

### Post by hyperair on 2007-09-01
If you wana remove Compiz Fusion, you gotta provide us with the way you installed Compiz Fusion in the first place. Different ways of installing have different ways of removing.

---

### Post by The Pinny Parlour on 2007-09-02
Thank you.  I used the CF Installer

---

### Post by The Pinny Parlour on 2007-09-02
I still can use Compiz-Fusion.  I have an icon and it all still works (minus a few plugins).

Can anyone shoe me how to rid COMPLETELY my system of this.

Thank you.

---

### Post by Forlong on 2007-09-02
> **The Pinny Parlour said:**
> I used the CF Installer
As far as I can tell from the code, there's an option to remove Compiz Fusion, if you run it again.

---

### Post by hyperair on 2007-09-02
*groans* Not that piece of junk. ><

Here's what you do.. you open a terminal in each of the subdirectories of /home/<YOURUSRENAME>/compiz. Then in each of them just run:
```

sudo make uninstall

```

When you're done, just remove the compiz directory from your home directory.

Now, the CF_installer.sh script is THE most buggy way of installing Compiz Fusion. You might like to try using one of the Compiz Fusion repositories for Feisty. (Trevino's, Vorian's or Amaranth's).

---

### Post by The Pinny Parlour on 2007-09-02
> **hyperair said:**
> *groans* Not that piece of junk. ><

Here's what you do.. you open a terminal in each of the subdirectories of /home/<YOURUSRENAME>/compiz. Then in each of them just run:
```

sudo make uninstall

```When you're done, just remove the compiz directory from your home directory.

Now, the CF_installer.sh script is THE most buggy way of installing Compiz Fusion. You might like to try using one of the Compiz Fusion repositories for Feisty. (Trevino's, Vorian's or Amaranth's).

Thanks for your help. *snip*, I wish then, that the MODS, ADMINS of the forums or whoever would let users of Compiz-Fusion know which is the correct one to install.

---

### Post by The Pinny Parlour on 2007-09-02
It didn't uninstall it.  I still have the icon showing up in the Applications menu.   It seems to have installed elsewhere on the PC.  Will go on a Search and Destroy mission.

---

### Post by hyperair on 2007-09-02
If you have the icon showing up its probably fusion-icon. Did you have a "fusion-icon" folder when you were on your uninstall mission?

By the way, I think you should go for Trevino's repostiories. They've got the best performance. Rather stable too =p

---

### Post by The Pinny Parlour on 2007-09-02
heaps of instances of it in the /usr folder but I can't delete them.  Something about permissions.

---

### Post by The Pinny Parlour on 2007-09-02
> **hyperair said:**
> If you have the icon showing up its probably fusion-icon. Did you have a "fusion-icon" folder when you were on your uninstall mission?

By the way, I think you should go for Trevino's repostiories. They've got the best performance. Rather stable too =p

Thank you I'm certainly going to try that next.  Just need to rid my Ubuntu of ALL compiz related junk.

---

### Post by Inxsible on 2007-09-02
First do this```
sudo apt-get remove --purge compiz* fusion-icon libcompizconfig*
```Then try ```
 locate *compiz*
```That will show you all the locations where compiz related files may be present. You can then delete each of them by

```
sudo rm -Rf /path/to/the/file
```For example I know for sure they are in /home/*username*/.gconf/apps/compiz. You can delete this folder without any problems since its in your own username, so you wont need any permissions.

Compiz also gets into /home/*username*/.config/compiz. Also check for /home/*username*/.compizconfig

The folders starting with . will not be visible, so you will need to press Ctrl + H in nautilus to see them.

Hope that helps !

[COLOR=Red]WARNING : Make sure you dont delete anything but compiz related stuff, or you might seriously bork your system[/COLOR]

---

### Post by The Pinny Parlour on 2007-09-02
I have worked out how to nuke folders.  rm name

---

### Post by The Pinny Parlour on 2007-09-02
Excellent.  Finally nuked the suckers out of my system.  Thanks to the guys who chimed in for advice.   Great stuff.
:):)

---

### Post by Vorian on 2007-09-02
> **The Pinny Parlour said:**
> Thanks for your help. *snip*, I wish then, that the MODS, ADMINS of the forums or whoever would let users of Compiz-Fusion know which is the correct one to install.
If you want to install Compiz Fusion in Feisty, the first choice would be compiling it from source.  If you insist on using a 3rd party repository, use Amaranth's repository.  He uses the same packages that are available in Gutsy.  I do not recommend using Trevino's repository.

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by hyperair on 2007-09-02
Well as far as I had heard, compiling from source is the method used if you know what you're doing. =P Otherwise, use precompiled DEBs. Anyway I'm a staunch supporter of Trevino's repository. I feel that Amaranth's is shortchanging the users, if by a little, due to the missing Compiz Fusion packages. Not to mention the performane hit I seem to be getting when using Amaranth's repository.

---

### Post by PriceChild on 2007-09-02
> **The Pinny Parlour said:**
> Thanks for your help. *snip*, I wish then, that the MODS, ADMINS of the forums or whoever would let users of Compiz-Fusion know which is the correct one to install.I'd like to point out that the mods and admins are just users like you... and many of us probably aren't as technically minded as you think.

I'd recommend using amaranth's repos ;)

---

### Post by steveneddy on 2007-09-02
> **Vorian said:**
> If you want to install Compiz Fusion in Feisty, the first choice would be compiling it from source.  If you insist on using a 3rd party repository, use Amaranth's repository.  He uses the same packages that are available in Gutsy.  I do not recommend using Trevino's repository.

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

I agree that compiling from source is the best way to run an application on any system, but I would like to add my vote for Trevinio's repos.

I have stayed with Trevinio since the Beryl days, and the fact that he usually has the most options as far as plug ins is a plus with me, and since is has always run well on my system, is why I vote for Trevinio.

I have performance issues with Amarath's.

---

### Post by steveneddy on 2007-09-02
> **hyperair said:**
> Well as far as I had heard, compiling from source is the method used if you know what you're doing. =P Otherwise, use precompiled DEBs. Anyway I'm a staunch supporter of Trevino's repository. I feel that Amaranth's is shortchanging the users, if by a little, due to the missing Compiz Fusion packages. Not to mention the performane hit I seem to be getting when using Amaranth's repository.

Agreed.

---

