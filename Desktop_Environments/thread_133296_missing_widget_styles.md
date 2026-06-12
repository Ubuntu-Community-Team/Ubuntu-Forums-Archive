---
title: "missing widget styles"
date: 2006-02-19
forum: Desktop Environments
---

### Post by manx801 on 2006-02-19
Hello,

I am running a stock Kubuntu 5.10 system. When I open the style configuration dialog in kcontrol, I only see the built-in styles: 

CDE
MS Windows 9x
Motif
Platinum
SGI

However, on my other Kubuntu 5.10 system, I see many more styles listed. As far as I can tell, both systems contain the same kde related packages. I am wondering why I don't see the full list, and how I might go about adding the additional styles on the system which seems to be missing them.

Any insight would be greatly appreciated. Thanks.

---

### Post by Ptero-4 on 2006-02-19
Are you sure that you got the kdeartwork package installed? That package contains the styles and windecos you mention.

---

### Post by manx801 on 2006-02-19
Yep. All of the kdeartwork packages are installed. I have also tried reinstalling them and this had no effect.

---

### Post by manx801 on 2006-02-23
Well, after a day or two of tinkering, I still am unable to access any styles in KDE except for the built-in ones. I have tried:

(1) complete removal and reinstall of KDE.

(2) complete removal and reinstall of qt related packages.

(3) upgrade to Dapper.

None of these efforts has made any difference in terms of getting the styles back. I have searched numerous forums, and have found some information about incompatibilities between qt and kdelibs that caused problems in the past. However, that does not seem to be the case here. 

Again, any help would be greatly appreciated. 
Thanks,

Paul

---

### Post by manx801 on 2006-02-24
Well, I went a bit further, and tried booting the live CD for Kubuntu (Dapper) and the styles are all available and working properly. 

So it seems that there is some remenant config file or link on my system which is causing the problem. This must not get updated or corrected when I completely remove and then reinstall the kde or Qt related packages which would imply that it is not part of those packages. 

Any suggestions about how I might figure out if there is a broken link, or corrupted config file associated with kcontrol and the style manager? Or better yet, could someone tell me a way to find all of the packages that are related to the syles in kde?

Thanks.

---

### Post by chikko on 2007-03-27
after a Kubuntu ordinary update yesterday night i can sadly say that it has happened to me as well.. - i'm using kubuntu feisty fawn, and till now my style was the default one (cannot remember it's name, but it was beautiful) - and now somehow i don't have it on the styles list - so it uses platinum or something..  pretty ugly..  :(

any suggestions to where or what should i config/install?

thanks very much!
chikko.

---

