---
title: "Recover evolution emails addresses etc?"
date: 2009-03-19
forum: General Help
---

### Post by rsullivan25 on 2009-03-19
Help - I lost my emails and contacts in Evolution and i don't know if I can get them back.  Here's what happened:

I've been having a problem for a few months where when I log into gnome my toolbars etc wouldn't display - I could log in with the "safe" gnome which disables startup scripts and everything worked ok.

Yesterday I found a website which explained that to restore the default ubuntu gnome settings all I had to do was:

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

Well I didn't remove these, I renamed them and was able to finally log into the default gnome desktop, however when I clicked on the evolution icon it brought up the wizard to set up a new account.

stupid me, I went through the wizard, thinking it might pick up my old settings but it seems that it overwrote them.  so my question is this:

Can I recover the overwritten settings  (emails, contacts, calendar etc)?  And if so, how do I get my old emails and contacts back into Evolution?

---

### Post by stchman on 2009-03-19
> **rsullivan25 said:**
> Help - I lost my emails and contacts in Evolution and i don't know if I can get them back.  Here's what happened:

I've been having a problem for a few months where when I log into gnome my toolbars etc wouldn't display - I could log in with the "safe" gnome which disables startup scripts and everything worked ok.

Yesterday I found a website which explained that to restore the default ubuntu gnome settings all I had to do was:

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

Well I didn't remove these, I renamed them and was able to finally log into the default gnome desktop, however when I clicked on the evolution icon it brought up the wizard to set up a new account.

stupid me, I went through the wizard, thinking it might pick up my old settings but it seems that it overwrote them.  so my question is this:

Can I recover the overwritten settings  (emails, contacts, calendar etc)?  And if so, how do I get my old emails and contacts back into Evolution?

Your emails are kept in ~/.evolution, Evolution's setting are in one of the folders you renamed.

---

### Post by Beefeater on 2009-03-19
I'm not using Evolution and can't really say if this will work.

You still got all your emails etc. in .evolution ?
So far so good.

Try to replace the folder $HOME/.gconf/apps/evolution with the old one.

---

### Post by rsullivan25 on 2009-03-19
Hi

Well I tried the replace option (saved the current one first) but it didn't do anything.

I looked at the ./evolution folder and some of the file sizes are really small.

ie in ./evolution/mail/local the Inbox file is 14.9 kb while Inbox.cmeta is 137 bytes.

getting worried that I somehow lost my email?

 I also found and Mbox import extension for thunderbird here [https://nic-nac-project.de/~kaosmos/mboximport-en.html](https://nic-nac-project.de/~kaosmos/mboximport-en.html) and tried to import some stuff out of the evolution folder but there's nothing there - there's a welcome email from evolution in the inbox and that's it.

Any other ideas?

Thanks in advance for everyone's help.

---

### Post by dcstar on 2009-03-19
> **rsullivan25 said:**
> 
.......
Yesterday I found a website which explained that to restore the default ubuntu gnome settings all I had to do was:

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

Well I didn't remove these, I renamed them and was able to finally log into the default gnome desktop, however when I clicked on the evolution icon it brought up the wizard to set up a new account.
......

This is now the second time I have seen a user lose their Evolution data because they "found a website...." etc and followed some bone-headed instructions.

If it was the same website from the other post then there are multiple comments following it **specifically stating that you will lose your Evolution data** if you do this - but people don't bother reading past the top lines.

The person who made this website should have removed these damaging instructions by now, otherwise more people will lose their data following this "advice".

---

