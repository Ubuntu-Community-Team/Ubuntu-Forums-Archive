---
title: "Stop displaying Link To in folder names."
date: 2009-05-11
forum: General Help
---

### Post by CowzRule on 2009-05-11
I'm running Hardy. How do I stop Nautilus from adding the "Link to" text when ever I create a link (shortcut) to a file or folder.
As you can see in the pic, the file "Link to Screenshot.png" is a shortcut to "Screenshot.png. The word "Link To" was automatically added to the files name. How can I stop that?

[IMG]http://i41.tinypic.com/adnpdl.png[/IMG]

---

### Post by SentientFluid on 2009-05-11
How are you creating the link? If you are right-clicking and selecting Make Link then you can't.  This is in place to avoid trying to create another file with the same name in the same folder (ie to prevent trying to have two files name "screenshot.png" in the same folder).  I believe it only happens when you try creating a link in the same folder as the target file.

If you want the link in a different location (which is usually the case), I believe if you middle-click "screenshot.png" and drag it onto the Desktop (for example) it will create the link without the "Link to" text.

I'm not at my computer so can't test it out, but I think that's how it works.

---

### Post by CowzRule on 2009-05-12
I create the links via the middle-click, drag, release, & select "Link Here". And that's going from one folder to a different one.

---

### Post by iKonaK on 2009-05-12
I am using Jaunty, and the "link to" only appears if i make the link in the same folder with the original.
Just F2 and delete the "link to" if it bothers you... :)

---

### Post by CowzRule on 2009-05-12
I want to make links to a bunch of files from one location to another and having to remove "Link to" on all of them seems dumb. Is there a way I can do it via the terminal?
I know the command "ln". Example "ln /home/cowz/screenshot.png /home/cowz/Desktop" will make a link to screenshot.png on my Desktop and without the "Link to" text. But say I have 10 files with different names, are there "wild cards" I can use in the command rather that having to do each file individually?

---

### Post by iKonaK on 2009-05-12
You can try renaming the links with [thunar's bulk renamer]("http://thunar.xfce.org/pwiki/documentation/bulk_renamer")   .

---

### Post by CowzRule on 2009-05-12
Thanks :)

---

