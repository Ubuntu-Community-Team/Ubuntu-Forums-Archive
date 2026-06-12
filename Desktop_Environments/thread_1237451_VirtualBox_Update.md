---
title: "VirtualBox Update"
date: 2009-08-11
forum: Desktop Environments
---

### Post by malty on 2009-08-11
I am attempting to update VBox 2.2.4, tried 3.04 first, GDebi says conflict with existing. Then tried 3.0, same result, I can understand the first but not the second, 3.0 is the next rung up from 2.2.4, any suggestions please.

---

### Post by andrea000 on 2009-08-12
Maybe update it from the update manager just add the 
ppa lines according to your distribution and update
it may work but that is the way i installed mine.you
will find them [here]("http://www.virtualbox.org/wiki/Linux_Downloads")

---

### Post by TransitMan on 2009-08-12
You will need to uninstall VirtualBox 2.2.4 first, then install VBox 3.04.
I tried with both Synaptic and by clicking on the .deb file, getting the same error message.
Hope this helps.

---

### Post by andrea000 on 2009-08-12
The deb is not what's in ubuntu by default that's
VirtualBox ose the deb is the full version and the
ppa line is alsoif you add the ppa line then install
that one from synaptic it will update the ose version
will not i think thats were the problem is

---

### Post by TransitMan on 2009-08-12
I have the ppa version listed in sources.list, and therefore do know what I have stated is correct.
Further, I am aware of the OSE version in the repos, and this version is not installed.

What I posted earlier about the error message is what i stand by, and apparently is what the the OP is experiencing also.
The last time i came across this problem on upgrading between VBox versions was from 1.xx to 2.xx, whereby the 1.xx version had to be uninstalled before the 2.xx version could be installed.

Under all circumstances, I had either used the ppa version, or the one from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads).

---

### Post by malty on 2009-08-12
I am not using the repo version, 2.2.4 is the deb version downloaded from th VBox site, as are the attempted updates.

---

### Post by TransitMan on 2009-08-12
> **malty said:**
> I am not using the repo version, 2.2.4 is the deb version downloaded from the VBox site, as are the attempted updates.

OK. Open Synaptic, search for Virtual Box.
When you find it, mark it for Complete Removal.
When it completes, close Synaptic, then install the .deb file of the latest VBox, 3.0.4.

---

### Post by andrea000 on 2009-08-12
> **TransitMan said:**
> I have the ppa version listed in sources.list, and therefore do know what I have stated is correct.
Further, I am aware of the OSE version in the repos, and this version is not installed.

What I posted earlier about the error message is what i stand by, and apparently is what the the OP is experiencing also.
The last time i came across this problem on upgrading between VBox versions was from 1.xx to 2.xx, whereby the 1.xx version had to be uninstalled before the 2.xx version could be installed.

Under all circumstances, I had either used the ppa version, or the one from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads).

I was not saying that you were not correct on yours.
I was saying on mine vb would update only after i
added the ppa and has updated good.

---

### Post by WilliamHaynes on 2009-08-19
when you un-install & then install 3.x do you loose all of your configurations and have to re-construction them?

thanks

---

### Post by linux4me on 2009-08-19
> **WilliamHaynes said:**
> when you un-install & then install 3.x do you loose all of your configurations and have to re-construction them?

thanks

Your configuration and your virtual machines are in the hidden file .VirtualBox in your home folder, which will not be deleted when you use Synaptic to uninstall and then reinstall the *.deb by double-clicking it. It will all be there when you start Virtual Box after the upgrade.

---

### Post by nomnex on 2009-11-14
Deleted

---

### Post by mikewhatever on 2009-11-14
Linux is case sensitive, so I think it's VirtualBox. Also try logging out and back in to, hopefully get the menu icon.

---

