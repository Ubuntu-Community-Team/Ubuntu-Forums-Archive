---
title: "Openoffice 2.0 Final is out."
date: 2005-10-20
forum: Deferred/Invalid Requests
---

### Post by TheDocMan on 2005-10-20
How about a backport of this for Breezy.  I believe Breezy shipped with a release canidate?

---

### Post by Jingo on 2005-10-21
I agree.

Don't know what bugs were solved. But it would be nice with this bug-fix upgrade.

---

### Post by MakubeX on 2005-10-21
The latest (source) I have was RC3 downloaded via CVS. If it is okay, I would like to request someone to give me the name of the milestone/release version here because I had no idea what to place in that specific CVS argument. The RC3's value is OOO680_m3, and the problem is I don't know the value for the Official Release 2.0. TIA!

---

### Post by Jeldert on 2005-10-21
OpenOffice.org 2.0.0 (final) == OpenOffice.org 2 RC3

---

### Post by jdong on 2005-10-21
The latest versions  all do not build properly on Hoary, starting from m100, and I've just simply struggled with them for too long. It takes up 9GB space and 6+ hours to figure out that a change wasn't successful etc etc etc.


I've backported 1.1.5 to Hoary, which provides you guys with OpenDocument support. As far as binaries for 2.0, there are scripts around the forum (debianize ooo) that can convert Openoffice RPMs to debs.

====

2.0.0 backport MAY be coming to Breezy.

---

### Post by themindlessmatt on 2005-10-22
Where can I get the 1.1.5 backport for hoary? Not in the official backport reps.
Thanks,
Matt

---

### Post by dabear on 2005-10-22
As far as the [norwegian version concerned](http://no.openoffice.org/), they provide debs. Strange that they don't for the english version :???: ( ? )

---

### Post by jdong on 2005-10-22
[QUOTE=themindlessmatt]Where can I get the 1.1.5 backport for hoary? Not in the official backport reps.
Thanks,
Matt[/QUOTE]

Good question... I sent it through the build engine and it never came out the other side :)

I'll get on that.

---

### Post by JuanC on 2005-10-23
Would be the OpenOffice 2 package compile with [GCJ](http://gcc.gnu.org/java) to don't need Java Sun Machine?

I hope this.

---

### Post by kleeman on 2005-10-23
For those interested. Test packages by Mathias Klose of Open Office 2 can be obtained by putting
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

in /etc/apt/sources.list

and then

sudo apt-get update && sudo apt-get upgrade

Works well on my box but remember it is a set of test packages.

More info here:

[http://lists.ubuntu.com/archives/ubuntu-devel/2005-October/012520.html](http://lists.ubuntu.com/archives/ubuntu-devel/2005-October/012520.html)

---

### Post by Bob D. on 2005-10-23
[quote=jdong]Good question... I sent it through the build engine and it never came out the other side :)

I'll get on that.[/quote] 
Any idea on the ETA for 1.1.5 for Hoary jdong? I keep checking but it hasn't made it to the repos yet. 

Thanks!

Bob

---

### Post by JuanC on 2005-10-24
I show that debian OpenOffice 2 Final packages , is also compiled with [GCJ](http://gcc.gnu.org/java) :

[http://packages.debian.org/unstable/editors/openoffice.org-base](http://packages.debian.org/unstable/editors/openoffice.org-base)


> 
Depends:
* java-gcj-compat
    Java runtime environment using GIJ


Is good idea that Ubuntu OpenOffice 2 packages will be also compiled with GCJ.

---

### Post by jasplund on 2005-10-24
[QUOTE=dabear]As far as the [norwegian version concerned](http://no.openoffice.org/), they provide debs. Strange that they don't for the english version :???: ( ? )[/QUOTE]

the DEB linked from no.openoffice.org are from [http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/RC3/](http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/RC3/) where you also can find english DEBs

---

### Post by dcstar on 2005-10-24
[QUOTE=jdong]Good question... I sent it through the build engine and it never came out the other side :)

I'll get on that.[/QUOTE]
I still can't see it.

---

### Post by jdong on 2005-10-24
[QUOTE=Bob D.]Any idea on the ETA for 1.1.5 for Hoary jdong? I keep checking but it hasn't made it to the repos yet. 

Thanks!

Bob[/QUOTE]

It seems like a last-minute build failure caused by some new library... I hate it when this happens.... The ETA for 1.1.5 will likely be pushed back until when Dapper opens, if not later, while the dependency problem is resolved with an OOo maintainer.


As far as OOo2 in Breezy, it is indeed compiled with GCJ.

---

### Post by rwabel on 2005-10-25
[quote=kleeman]For those interested. Test packages by Mathias Klose of Open Office 2 can be obtained by putting
deb [http://people.ubuntu.com/~doko/OOo2]("http://people.ubuntu.com/%7Edoko/OOo2") ./

in /etc/apt/sources.list

and then

sudo apt-get update && sudo apt-get upgrade

Works well on my box but remember it is a set of test packages.

More info here:

[http://lists.ubuntu.com/archives/ubuntu-devel/2005-October/012520.html]("http://lists.ubuntu.com/archives/ubuntu-devel/2005-October/012520.html")[/quote]

works fine! thanks

---

### Post by andrewpmk on 2005-11-13
Now that Breezy Backports is open (but empty), could someone backport OpenOffice 2.0 to Breezy?

---

### Post by jdong on 2005-11-13
[QUOTE=andrewpmk]Now that Breezy Backports is open (but empty), could someone backport OpenOffice 2.0 to Breezy?[/QUOTE]

This has already been requested several times -- it has to be in Dapper first. And 30+ packages have been filed for build and upload, though James Troup is busy off at UBZ.

---

### Post by andrewpmk on 2005-11-13
Is there someone else with the appropriate permissions that could do this instead?

---

### Post by jdong on 2005-11-13
-- Matthias Klose <doko@ubuntu.com>  Sat, 8 Oct 2005 10:21:41 +0000

^^^^^ Ubuntu Openoffice.org Maintainer ^^^^^^

---

### Post by mantiena on 2005-12-06
[QUOTE=jdong]This has already been requested several times -- it has to be in Dapper first. And 30+ packages have been filed for build and upload, though James Troup is busy off at UBZ.[/QUOTE]

So, OpenOffice.org 2.0.1 is already uploaded to Ubuntu Dapper, are there chances to get breezy backport?

If so, maybe I could help ?

---

### Post by macleod199 on 2005-12-06
[QUOTE=mantiena]So, OpenOffice.org 2.0.1 is already uploaded to Ubuntu Dapper, are there chances to get breezy backport?

If so, maybe I could help ?[/QUOTE]

For the record it's a 2.0.1 *release candidate*. I imagine backports will at least wait for a stable version.

---

### Post by jdong on 2005-12-06
Well, I believe that depends on exactly how stable the 2.0.1 package is compared to Breezy's.

---

### Post by teb on 2005-12-07
I had already included the [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) repository to run OO.org2 on my Breezy laptop a few weeks ago. I did this because my OOo2 didn't work well: in the beginning (fresh Breezy install) it did work; after adding a few applications (amongst others Eclipse) I ran into trouble:

OOo2 does start up but when editing some of the contents a a documents (text, calc, etc) it hangs and I need to force it to quit.

So I added the doko repository and still it didn't improve.

How could I find out where the problem is? Is there some dependency that might mess it up? I uninstalled a few programs like eclipse, as it uses other java libraries, but that didn't work either.

BTW In the Backports repository I don't find OOo2, but version 1.9.129. I'm using :
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
Is that correct?

So downgrading to 1.9.129 my office suite works again (and I'm not required to run 1.1.5 ;-)

thanks, Wouter

---

### Post by QuacoreZX on 2005-12-29
wait wait...so which build is [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) applicable for? It's some test deb's for...Hoary? Breezy? o_O sorry for my confusion....

---

### Post by jdong on 2006-01-02
Those are for Breezy, 2.0 final.

2.0 updates are not being considered for Hoary due to technical limitations (Java)

2.0.1 updates for Breezy are being considered through breezy-updates currently, with Backports being a secondary fallback.

---

### Post by epineda on 2006-07-05
I use the following repository in /etc/apt/sources.list for 2.0.2 backport to breezy:

deb [http://people.ubuntu.com/~doko/ubuntu](http://people.ubuntu.com/~doko/ubuntu) breezy-updates/

---

