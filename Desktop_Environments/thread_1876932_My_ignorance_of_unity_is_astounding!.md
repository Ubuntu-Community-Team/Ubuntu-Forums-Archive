---
title: "My ignorance of unity is astounding!"
date: 2011-11-07
forum: Desktop Environments
---

### Post by ajaxdude on 2011-11-07
Just throwing this out: My ignorance of unity is astounding!
I was using some other versions of Ubuntu, and my Linux background predates Fedora, back to Redhat 7.

I'm annoyed about things that I need to figure out, things that I don't think I should have to figure out. In other words, I'm annoyed about things that should be intuitive, but are not, that I feel are flaws, in an otherwise amazing distro. Maybe I just don't grok it. 

The software provided through the channels is not a "one-stop-shop." Which leads to another problem, the whole dash thing, it refuses to see any binary files, or folders containing therein. For example, I'm trying out Aptana, but I could not find it from Synaptic, so I downloaded, ran it from a folder, but- I can't see that folder from the dash. I have the same problem with Eclipse, I want to use Eclipse EE not eclipse so I have installed that as well. Is there some tool for updating the database of apps that Unity is aware of, unity command line tool? Or a GTK application that manages this?

I've googled this stuff, and I keep running into blogs about what people are doing after installing Ubuntu.  Would people stop writing those already!

---

### Post by Copper Bezel on 2011-11-07
If this isn't the best solution, I blame the fact that it's being posted out of sheer insomnia, but.... = )

If an application isn't installed by the usual means, it probably won't create a .desktop file in /usr/share/applications, which is the only way for Unity's dash (or Gnome 2's Alacarte menu editor, for that matter) to find it. However, if you run alacarte from a terminal (comes up in the dash as Main Menu) you can create an entry there, and it'll appear in the dash. Otherwise, you can just write a custom .desktop file in ~/.local/share/applications.

Generally, applications installed from the Software Center or other methods using repositories and PPAs will create .desktop files during installation. However, since there are so many Linux desktops and ways of handling these things, not every application does this, because there's a lot of software that doesn't take the Gnome desktop into account.

It's not that anything is "refusing" to show binary files - there are a lot of executable files on your computer that wouldn't be pertinent in the dash. = ) If an application isn't set up to make itself accessible to the DE, you have to do the extra work for it.

---

