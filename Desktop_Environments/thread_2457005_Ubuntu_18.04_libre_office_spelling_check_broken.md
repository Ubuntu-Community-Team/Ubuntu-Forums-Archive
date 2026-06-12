---
title: "Ubuntu 18.04 libre office spelling check broken"
date: 2021-01-23
forum: Desktop Environments
---

### Post by jimhce on 2021-01-23
Hi,

I installed Ubuntu18.04 with Libre Office version 6.0.7.3 Build ID: 1:6.0.7-0ubuntu0.18.04.10, but it could not run spelling check. Appreciate your advise how to fix it?

Thank you.

Kind regards.

---

### Post by ActionParsnip on 2021-01-24
Why did you not install Ubuntu 20.04? This is also LTS and supported 2 more years after 18.04 support ends.

---

### Post by ActionParsnip on 2021-01-24
What happens when you try to run a spellcheck? Do you see any errors or warnings?

---

### Post by jimhce on 2021-01-24
> **ActionParsnip said:**
> What happens when you try to run a spellcheck? Do you see any errors or warnings?

No, it did nothing.

For question why I did not install 20.04, because the laptop is used for embedded system software firmware development, it needs to use the same version as the build server.

Thank you.

Kind regards.

---

### Post by ajgreeny on 2021-01-24
Check to see if you have the needed "spell" packages installed, eg, hunspell or one of the others; not on a buntu system at present so can't check what I have but I'm sure hunspell is one of them, maybe aspell as well.

---

### Post by Hagar Delest on 2021-01-24
See if that helps: [[Tutorial] Spell check and Language configuration]("https://forum.openoffice.org/en/forum/viewtopic.php?f=74&t=67").
Depending on your findings, it will help investigate if it's a package issue or a mere LO configuration issue.

---

### Post by jimhce on 2021-01-25
I think the spell packages are installed, right?
$ dpkg -l | grep spell
ii  aspell                                     0.60.7~20110707-4ubuntu0.1                       amd64        GNU Aspell spell-checker
ii  aspell-en                                  2017.08.24-0-0.1                                 all          English dictionary for GNU Aspell
ii  dictionaries-common                        1.27.2                                           all          spelling dictionaries - common utilities
ii  enchant                                    1.6.0-11.1                                       amd64        Wrapper for various spell checker engines (binary programs)
ii  hunspell-en-us                             1:2017.08.24                                     all          English_american dictionary for hunspell
ii  libaspell15:amd64                          0.60.7~20110707-4ubuntu0.1                       amd64        GNU Aspell spell-checker runtime library
ii  libenchant1c2a:amd64                       1.6.0-11.1                                       amd64        Wrapper library for various spell checker engines (runtime libs)
ii  libgspell-1-1:amd64                        1.6.1-1                                          amd64        spell-checking library for GTK+ applications
ii  libgspell-1-common                         1.6.1-1                                          all          libgspell architecture-independent files
ii  libhunspell-1.6-0:amd64                    1.6.2-1                                          amd64        spell checker and morphological analyzer (shared library)

---

### Post by Hagar Delest on 2021-01-25
I've never bothered checking that in fact.
See if you do see the checkmarks in the LO dialog that tells that the desired language is available/active or not.
Resetting the LO profile may help. It is a standard fix in AOO, not sure if it has the same advantage with LO.

---

### Post by Dennis N on 2021-01-25
In my Ubuntu 18.04, I installed the Flatpak version and removed the repository version of LibreOffice. The spell check works in the Flatpak version (currently 7.0.4.2). So you could use that.

---

### Post by ajgreeny on 2021-01-25
Check your settings in the LO -> Tools -> Options -> Writer to see what you have in the ***Language*** and ***Writing Aids*** sections.

Here's what I see in my LO and spell check works well.

---

### Post by jimhce on 2021-01-26
I have exactly the same except of English (USA)

---

### Post by ajgreeny on 2021-01-26
I also have an icon in my toolbar which allows me to toggle the spellchecker display off and on.
Do you have the same icon, and is it set to Off?

---

### Post by Hagar Delest on 2021-01-26
In the tutorial I've linked, do you see all the check marks where they should be?
There is a quicker tutorial for the record, linked in the first post of the main tutorial.
What are the symptoms BTW? Do you see the red wavy lines?

---

