---
title: "ubuntu deployment in the workplace"
date: 2006-01-16
forum: General Help
---

### Post by straylite on 2006-01-16
Hi

This is my first post to these forums so please forgive me if this topic has appeared elsewhere.

I have an office of five staff and I'm planning on switching at least some of us to ubuntu fairly soon. Whilst our development team is quite capable of making the change and managing all of the implications in switching to linux, our non-development staff won't be. So I have some questions:

1. I've discovered that I will probably need a load of packages that (for one reason or another) do not come with the standard ubuntu distribution: things like fonts, WINE and so on. Is it possible to make a CD that has packages in addition to the primary distribution, or is there a way that I could batch-deploy these packages? I'm thinking that some will be available through apt-get, but others would just have to be downloaded and installed through a script?

2. I've found that there is an issue with fonts in Linux. We're a web design business and for some reason some of our work doesn't render 100% correctly in Firefox under Linux, with the standard fonts that come with it. Is this because I haven't installed the Microsoft TrueType fonts package? For an example, look at the primary nav on [www.redwiredesign.com](www.redwiredesign.com) in Firefox/Win and the same in Firefox/Linux. The text spacing is wonky, and the rest of the text on the page looks different too. This may just be unthought-out design, but I'm wondering if anyone else has come across this issue.

Thanks for your help!

j.

---

### Post by briancurtin on 2006-01-16
1. you could pop them on a CD, and install them from the path to your CD drive. you could write a script to install everything off that CD to make things easier if you wanted.

2. i dont know much about this, and i dont have these fonts, but it does seem like you would want the MS true type fonts for something like this. dont take my word for it, as hopefully somone after me has a better idea, but i would at least try the MS TTF and see how they work.

---

### Post by straylite on 2006-01-16
Thanks; I'll give the CD thing a go... I guess it'd probably be some sort of post-install script like you can do with XP cds.

---

### Post by newuser111 on 2006-01-16
for ms true type fonts do sudo apt-get install msttcorefonts

---

### Post by slux on 2006-01-16
Ehm, you can't depend on some fonts being universally available if they're something just MS supplies (and I assure you that few Linux users have msttfcorefonts installed). You either need to make sure that your page layout doesn't go wrong with several different fonts or choose one that is certainly available for all (Windows, Mac, Linux, etc.)

A slight layout glitch is not so bad if the website functions properly otherwise though. Still, if you're a web design business that wants to do your job well you should cope...

You can use "dpkg --get-selections > selections.txt" on a a machine that has it all already installed and "dpkg --set-selections < selections.txt" with "apt-get dselect-upgrade" on others for aptable packages that you want to install on all your systems.

If you have more customization needs, look into a cloning package such as replicator that lets you clone a preinstalled machine. It's also faster than doing a standard Ubuntu install (although maybe not that much faster than the new OEM install) but may not be worth the effort if you only have a few machines to install on.

---

### Post by az on 2006-01-16
Here is how to create a cd with packages on it:
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

You can use that cd as an apt-source in synaptic.  But, if all the computers are on a network, just use one of them as a repo.  The box that you use to make the cd from can just as easily be an apt source.  Why make a cd?

And if you set up apt right, you dump packages into your local repository and all of your boxes sync up.  They automatically get their updates (or new packages) from the local repo.

---

### Post by Gowator on 2006-01-16
Firstly the site look fine to me using firefox 1.07 though I do have some extra fonts installed (just added the stuff in automatix)

Largely it is a question of if you name fonts in the design.  
If you do this then MS core fonts are usable but then you require those browsing either have them or will get substitution....

Basically you need to have some descisions ... you use of flash would preclude myself from using you because I usually find a flash page and simply try the next until I find someone not using flash.  

However this is up to you, I am just pointing out you have chosen to limit who can view the page and hence have predecided not to make it available to everyone so I wonder why a small matter like fonts being out of place bothers you when people who choose not to have flashplayer extensions installed will not be able to see the page at all?  

Why not just put a best viewed with Internet Explorer logo or at least have different pages for different browsers.  

Let me put it this way, even though I have flash installed I would subscribe and pay money to a service that filtered sites with flash out of my google searches ...

On extra software its so simple its hardly a challenge...
First way Just write a bash script with apt-get install (and then a list of the packages) 
I would have it one per line so that its easy to see what fails if a repo is down... If you have decent internet access (I have ADSL2 and get about 20Mbit/sec) then it takes hardly any time to add packages.  The config part takes longer

A second way is to use apt-cache and build a local apt mirror ... this makes sure the versions are the same and prevents problems is a repo is unavailable.  

A third way is simply to clone the install ... partimage does a good job and then just restore the whole image .. this is OK so long as your base packages stay the same ... and if you have a lot of customized changes... 

Third way is using remote desktops for the most have windows apps.  I'm presuming you will keep macromedia etc.  but you can run these remotely on a server either using a Windows server like metaframe and ICA or running a vmware session and using that... there are a **lot** of possibilities all depending on your budget.  You could also use a OS-X version of the SW for instance on cheap headless minimac... which would integrate better.

I would avoid using individual wine installs because its fiddly and easily broken and your developers want to spend time developing not fixing wine ... Im not saying don't use Wine.here.Im saying don't use it as a first resort when 5 people are using the same apps because its better to have a single centrally configured app ...

Finally ... don't expect a single day switch over... I have done a lot of migrations (professionally) and even tech people will need change management and non-tech people quite a bit.  
As an example you will need to decide how limited software will be .. will you leave a functional desktop or lock it down... wilæl users browse for their own printers or have them installed... 
(it is my considerable experience that web developers and tech people will resent too much standardisation and it becomes counter productive to stop a web designer for instance changing the screensaver or background... )

---

