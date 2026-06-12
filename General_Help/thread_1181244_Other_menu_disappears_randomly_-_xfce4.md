---
title: "Other menu disappears randomly - xfce4"
date: 2009-06-07
forum: General Help
---

### Post by barisurum on 2009-06-07
Hi;

I have a very annoying problem with xfce4. When I boot into it everything is OK. I can reach the other menu. But after a while it just vanishes! I have to logout and login again to reach it again. Thanks in advance.

PS: I didn't install xubuntu-desktop just did a minimal install with xfce4 metapackage.

---

### Post by kerry_s on 2009-06-07
> **barisurum said:**
> Hi;

I have a very annoying problem with xfce4. When I boot into it everything is OK. I can reach the other menu. But after a while it just vanishes! I have to logout and login again to reach it again. Thanks in advance.

PS: I didn't install xubuntu-desktop just did a minimal install with xfce4 metapackage.

other menu? desktop? panel? 
install xfce4-screenshooter and give a pic please, i have no idea what your talking about.

---

### Post by barisurum on 2009-06-07
:) other is the name of a sub menu in xfce4 menu where applications unidentified (or couldn't be identified) by xfce4 are put. 
But nevermind I solved the problem by editing my custom .menu, .directory and .desktop files in my home/.config and .local directories and I'm the master of the universe now! :D :popcorn: ):P :KS

---

### Post by tinmice on 2010-06-15
Sorry to dig up old posts. I'm having similar problems still on 10.04. If you right clikc on the menu button and customise, you can choose which menu file it points to. I tried pointing it to the 'custom menu file' option located in /etc/xdg/menus/xfce-applications.menu . I didn't know you could do this before so tried to get rid of a few things I don't use, such as the help and about links, but the whole thing just went a bit random and put a couple of help things in higher up the list etc. What did you edit and do you need to manually add an application every time you install something?

Cheers.

---

### Post by GOwin on 2010-06-16
I experience the same annoying bug.

My workaround is to remove the XFCE menu button from the panel and then add it back again to restore the Other sub-menu.

---

### Post by Kent Asplund on 2010-10-12
> **GOwin said:**
> I experience the same annoying bug.

My workaround is to remove the XFCE menu button from the panel and then add it back again to restore the Other sub-menu.
I tried it but next time I login then it dissappears again. :(

---

### Post by MonkeyZazu on 2010-12-05
> **Kent Asplund said:**
> I tried it but next time I login then it dissappears again. :(

hey, are you still having this problem? here is my fix, and this is pretty much for anyone still having this problem( disappearing other menu in xubuntu or other xfce environment distro). this is how i got my other menu to not disappear anymore.

The guy who posted this thread said that he edited his "custom .menu, .directory and .desktop files in my home/.config and .local directories", so i started looking in those directories for those files. 

So first I went to this directory:

```
zazu@zazu-laptop:~$ cd .local/share/applications/
```

listed everything, and got all these .desktop files

```
zazu@zazu-laptop:~/.local/share/applications$ ls
defaults.list                             wine-extension-ppsx.desktop
Microsoft Office Excel 2007.desktop       wine-extension-ppt.desktop
Microsoft Office PowerPoint 2007.desktop  wine-extension-ppthtml.desktop
Microsoft Office Word 2007.desktop        wine-extension-pptm.desktop
mimeinfo.cache                            wine-extension-pptx.desktop
wine                                      wine-extension-pptxml.desktop
wine-extension-cdf.desktop                wine-extension-prf.desktop
wine-extension-chm.desktop                wine-extension-pwz.desktop
wine-extension-csv.desktop                wine-extension-rat.desktop
wine-extension-dic.desktop                wine-extension-rels.desktop
wine-extension-doc.desktop                wine-extension-rtf.desktop
wine-extension-dochtml.desktop            wine-extension-sct.desktop
wine-extension-docm.desktop               wine-extension-sldm.desktop
wine-extension-docx.desktop               wine-extension-sldx.desktop
wine-extension-dot.desktop                wine-extension-slk.desktop
wine-extension-dothtml.desktop            wine-extension-thmx.desktop
wine-extension-dotm.desktop               wine-extension-txt.desktop
wine-extension-dotx.desktop               wine-extension-URL.desktop
wine-extension-dqy.desktop                wine-extension-vcf.desktop
wine-extension-exc.desktop                wine-extension-wab.desktop
wine-extension-gif.desktop                wine-extension-wbk.desktop
wine-extension-hlp.desktop                wine-extension-wri.desktop
wine-extension-htm.desktop                wine-extension-wsc.desktop
wine-extension-html.desktop               wine-extension-xevgenxml.desktop
wine-extension-ini.desktop                wine-extension-xla.desktop
wine-extension-iqy.desktop                wine-extension-xlam.desktop
wine-extension-jfif.desktop               wine-extension-xlk.desktop
wine-extension-jpe.desktop                wine-extension-xll.desktop
wine-extension-jpeg.desktop               wine-extension-xlm.desktop
wine-extension-jpg.desktop                wine-extension-xlsb.desktop
wine-extension-mpf.desktop                wine-extension-xls.desktop
wine-extension-p7b.desktop                wine-extension-xlshtml.desktop
wine-extension-p7c.desktop                wine-extension-xlsm.desktop
wine-extension-png.desktop                wine-extension-xlsx.desktop
wine-extension-pot.desktop                wine-extension-xlt.desktop
wine-extension-pothtml.desktop            wine-extension-xlthtml.desktop
wine-extension-potm.desktop               wine-extension-xltm.desktop
wine-extension-potx.desktop               wine-extension-xltx.desktop
wine-extension-ppa.desktop                wine-extension-xlw.desktop
wine-extension-ppam.desktop               wine-extension-xml.desktop
wine-extension-pps.desktop                wine-extension-xsl.desktop
wine-extension-ppsm.desktop

```

All of these files are pretty much the same by the fact that they all had this line in them:

```
NoDisplay=true
```

so i just edited one of these files so that the "true" was changed to "false".

Right after i did this my other menu came back and has not disappeared sence. Hope this helped everyone!:)

just message me if you need more info.

---

### Post by jgor on 2011-07-13
I had this problem and it is very annoying. For me the "other" menu disappeared every time I ran a Windows program in WINE. My solution was quite drastic since I was very irritated with this bug, I upgraded to XFCE 4.8 using the help on this page: [http://www.multimediaboom.com/how-to-install-xfce-4-8-xubuntu-in-ubuntu-10-10-10-04/](http://www.multimediaboom.com/how-to-install-xfce-4-8-xubuntu-in-ubuntu-10-10-10-04/) .

Warning! This may cause more problems than it fixes and you may be finding yourself needing to revert back to 4.6 (which shouldn't be too hard).

In my case upgrading to XFCE 4.8 solved the problem of the "other" menu disappearing and actually fixed a completely different problem which was unexpected (my laptop monitor can now be dimmed and brightened with the proper keyboard shortcuts).

I hope this helps others solve this problem.

---

### Post by ctg60 on 2011-12-30
I have exactly the same issue. The 'Other' sub-menu in my XFCE4 main menu disappear mysteriously sometimes. Thanks to MonkeyZazu's hint. I modify some of my home cooked .desktop files in ~/.local/share/applications folder, adding some of the fields like Encoding, NoDisplay specifically. The 'Other' menu appears again immediately without system reboot. I believe this issue is due to the incompleteness or syntax error of some of the .desktop files.

---

### Post by ctg60 on 2011-12-30
I spoke too soon. The 'Other' sub-menu disappeared again about 20 minutes later after that. Then I try to modify the content of the ~/.local/share/applications folder again, and the 'Other' menu apprears again right after the modification. This make me to believe the modification cause XFCE to sync the menu again. That is why we could see the 'Other' menu again. 

Besides I find that we could use the command **desktop-file-validate** to validate the .desktop files.

---

