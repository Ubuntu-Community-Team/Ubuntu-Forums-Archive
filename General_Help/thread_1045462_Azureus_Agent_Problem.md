---
title: "Azureus Agent Problem"
date: 2009-01-20
forum: General Help
---

### Post by Nosophorus on 2009-01-20
Hi!

I have uninstalled Azureus and I keep receiving annoying informations from its agents. See it at the link below (the agent is at the screen bottom right):

[http://img103.imageshack.us/img103/631/azureusagent2md9.jpg](http://img103.imageshack.us/img103/631/azureusagent2md9.jpg)

I uninstalled Azureus through the command:

sudo apt-get autoremove --purge azureus

And I deleted manually all the directories/folders (and some files too) related to azureus which were not removed by the command above.

But, despite that, it seems the agent has not been deleted -- or something like that.

How should I proceed to remove the agent?

Thank You!

---

### Post by taurus on 2009-01-20
Did you also remove ~/.azureus (or /home/marcelo/.azureus)?

---

### Post by Nosophorus on 2009-01-20
Hi!

Yes, I removed the ".azureus" folder inside my home folder. See:

marcelo@marcelo:~$ pwd
/home/marcelo
marcelo@marcelo:~$ cd .azureus
bash: cd: .azureus: Arquivo ou diretório inexistente

Arquivo ou diretório inexistente = File or folder does not exist.

After uninstallaing Azureus, another strange behaviour I have noticed is my internet connection keeps sending and receiving bytes intermittently, despite I am not aware of a program trying to access it. Is there some way to see what programs are actually sending/receiving bytes?

Thank You!

Marcelo

---

