---
title: "KDE 3.4.1 Authentication"
date: 2005-06-24
forum: Desktop Environments
---

### Post by chenlevy on 2005-06-24
It is official now. I am trubbeld.

I spend a perfectly good weekend's afternoon searching for the anser in the forums and google, and I came to the conclusion that no one cares.

I want KDE 3.4.1, I realy do, but not as mutch to ignore the "WARNING: The following packages cannot be authenticated!" message, the sad thing is it seems that I am the only one that cares.

Yes, I know. These are not official packages. I dont expect them to be signed by the ubuntu / kubuntu "master" key. I just want to know if they are signed at-all. And if so, with what key? And how do I make this key known to the apt / dpkg? Is it /etc/apt/secring.gpg?

Then I will be able to ask around and figure out if I trust this key. I can hope then that the same person / group will create the 3.4.2 pacakges, thus I limit my exposure.

Ideas? Comments?

Cheers,
Chen.

---

### Post by wdso on 2005-06-24
To be honest, you're just being paranoid here  ](*,) 

Backports packages aren't signed either, explanation is (according to the FAQ):

> 12) Ok, I'm using Hoary Backports, but APT always says 'WARNING: Package cannot be authenticated.' Why's that?
Hoary uses APT signing to authenticate its packages. I do not have such an infrastructure set up yet. If anyone can point me to some good articles about this, or have information on how I can implement this easily, or disable the message, please E-Mail me.

I guess its simply not worth the effort for experimental packages. Its much more likely, that the packages themselves compromise your system, Therefore, if you really want to have a secure system (but don't forget: total security is an illusion), stick with the official packages.

---

### Post by chenlevy on 2005-06-25
wdso, first I want to thank you for your reply. Thank you also for referring me to the backports project and the backports project FAQ at [http://backports.ubuntuforums.org/faq.php](http://backports.ubuntuforums.org/faq.php).

Having done so, let the nitpicking begin:

0) Testing packages can trash my system, but installing untrusted binaries may compromise it, which is completely different ball of wax.

1) Cryptographic authentication *is* important even in non official / testing packages.

Both KDE 3.4.1 from:
deb [http://download.kde.org/stable/3.4.1/kubuntu](http://download.kde.org/stable/3.4.1/kubuntu) hoary-updates main
And the backports project in:
deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) hoary ...
are mirrored on multiple hosts, each of which can be compromised.

Signing packages before they are propageted to the mirrors, effectively blocks that attack vector, and reduces the hazard of man in the middle attacks.

2) I am comming to ubuntu from using APT in the Red Hat realm. There it was a simple matter of getting the public key from the third party repository (fedora-legacy, kde-redhat, at-rpms, etc.) and importing it using gnupg or rpm. While on the repository part it was a simple matter of `rpm {--addsign|--resign} PACKAGE_FILE ...`
I find it hard to believe that this is much harder in debian land, where the packaging tool is legendary.

3) Links to KDE 3.4.1 (both the apt  repositories <http://kubuntu.org/hoary-kde-341.php> and the live CD version <http://kubuntu.org/special-cds.php>) are prominently displayed in the kubuntu.org site. It make them seem as at least semi-official. If they are not, that means that the next official release breezy will be KDE 3.5 and thus no bug-fix translation version will be official (note that even a boring release like KDE 3.4.1 has significant translation changes, witch is important to any non English speaking user). For me, kubuntu is debian with an up-to-date KDE. I hope it will really be that, because other wise, my distro nomad days are not over yet.

4) If nothing else, encouraging users to use unsigned packages, is to teach them bad practises, and isn't any better then the security practises of average users in Windows-land. We can and should do better.

* * *

I want to be clear. Ubuntu and kubuntu are a grate gift for me as a user, and for all it's users. I want to thank all the developers and contributers for doing a grate work, but not signing packages is simply wrong, and I hope it will be fixed soon.

Thanks for reading.
Cheers,
Chen.

P.S. The fact that I am paranoid doesn't necessarily mean, that there aren't any people that trying to get me.

---

### Post by elsewhere on 2005-06-25
[QUOTE=chenlevy]
4) If nothing else, encouraging users to use unsigned packages, is to teach them bad practises, and isn't any better then the security practises of average users in Windows-land. We can and should do better.

[/QUOTE]

True, but as Windows also demonstrates, teaching users that a signed package can be trusted is equally bad.  A number of spyware/adware applications are happily installed by users that click yes on the ActiveX box because the vendor took the time to sign their package.

Your post shows you understand the concept of "trust" behind package signing, but I think the majority of new or even intermediate users don't, and assume things are black and white.

I'll admit that it's unnerving to get the unsigned package warning, but my trust level comes from this community.  I know there are numerous ways that the mirrors can be compromised et al., but I manage that risk against my desire to use the newer packages, just as I do when I download apps from kde-look or kde-apps.org.  I trust that if a package was discovered to be compromised, that it would be detected and users alerted.  It's not a naive choice on my part, since I know the inherent risks, just a compromise I'm willing to make.

I would also go as far to say that new users probably shouldn't be encouraged to use apps outside of the official Ubuntu repositories, not until they get their skill level and experience up to a moderate level.  Ubuntu is very specific on the packages they sponsor and endorse for their distribution, anything else is more or less buyer beware.  I think they make a reasonable effort to make that clear.

So I'm not disagreeing with anything you're saying, just just trying to present a balanced view.  Security always boils down to a risk - management equation, how much security do you need at the cost of convenience / useability.  Doesn't matter whether it's a home user or global enterprise.  New users may not be able to manage the risk properly and should probably err on the side of caution, even if it carries a cost of less flexibility or useability (ie. not downloading or installing third-party apps).  Others, such as you or I, can make an educated choice about whether to or not.  Choice rules.

Having said all that, have you checked the Breezy repositories ?  I know 3.4.1 was uploaded, and while I haven't checked myself, it may be signed.  Not sure if 3.4.1 compiled for Breezy could cause conflicts with Hoary, but might be worth a look ?

Cheers,
KV

---

