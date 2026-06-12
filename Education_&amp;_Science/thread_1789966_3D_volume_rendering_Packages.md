---
title: "3D volume rendering Packages"
date: 2011-06-24
forum: Education &amp; Science
---

### Post by kaspar_silas on 2011-06-24
Anyone used or have any advice on medical 3D rendering packages. Specifically for packages that can produce 3D rotatable renderings from a stack of dicom slices/raw data?  There are loads of packages available so I am just looking some recommendations really.

Cheers,



p.s.
I used to use Osiris but moved workplaces and now don't have any Macs about. I assumed Osiris would be compilable for other OS but (somewhat surprisingly for an large open source project) it seems OsiriX isn't interested in cross platform compatibility:

[http://www.osirix-viewer.com/OsiriXForWindows.html](http://www.osirix-viewer.com/OsiriXForWindows.html)  

Fair enough I guess thou IMHO that's a slightly childish stance for a medical data viewing program.

---

### Post by Stefanbanev on 2011-06-24
I would recommend HDVR(R); it provides the highest interactive rendering quality for the huge view ports and practically unlimited data size (up to 4K cube) and you may go to any number of slices with 4D. 3GB/i7 laptop may render interactively at high quality 4k CT data. If you are researcher from  university you may apply for research licence: [http://forms.fovia.com/forms/register.php?t=research](http://forms.fovia.com/forms/register.php?t=research)
To have the highest interactive quality the sufficient CPU resources are a mandatory to have like <dual i7x6cores> (GPU is irrelevant). The interactive rendering quality is way higher over any other solution on the market; besides, the build-in tool set is very extensive and versatile to build virtually any workflow you would like.

//-----------
The supported platforms:
Windows 7, XP 64/32
Linux 64/32: Red Hat Enterprise Linux (CentOS and Fedora compatible), Ubuntu Desktop Linux
Macintosh OSX 64/32

The following deliverable types:

Client/Server/Workstation application
C++ Client/Server API
Java Client/Server API
.NET Client/Server API (Windows only)
C++ In-Process API
Transfer Plugin API
Server API
OsiriX Plugin (OSX only)
It is available in two editions:
x2 Transfer Function version
x8 Transfer Function version (new)

---

### Post by kaspar_silas on 2011-07-01
Well okay that certainly looks pretty damn amazing and I am a researcher so I may certainly give it a try. 

Two quick questions:

Are you sure it supports ubuntu. The website only states support for Red Hat,MS and OS. Admittedly switching to Red Hat is not exactly impossible. Then again I do like ubuntu and everything else is set up on it.

Secondly I didn't see any C++ code examples or documentation on the website so I have no feel for the level or how obvious the SDK is. Do you have any experience on this. I mean to make a example case will it cost me 10, 100 or 1000 lines of code.

---

### Post by Stefanbanev on 2011-07-01
>Are you sure it supports ubuntu.

Positive... specifically, I run the latest HDVR client/server build under Ubuntu Desktop 10.10 x64, the 32bit was in the package as well (I did not test 32bit version). Besides its incredible interactive quality I have virtually the same performance for small and for huge data-sets (above 1K cube) with view port ~1.5MP. It should be noted, even they require some relatively modest minimum hardware specs, to get a high quality interactive rendering you need to have a sufficient CPU, my WS is dual X5650 (just build from superbiiz.com). The interactive rendering quality is quite astonishing, it blows away all GPU engines I've benchmarked under GTX580/3GB (Windows7/64).

>I have no feel for the level or how obvious the SDK is. Do you have any experience on this. I mean to make a example case will it cost me 10, 100

Well, I played with client/server C++ SDK, just the Fovia code part takes under 100 lines to get a simple client/server viewer, the java version maybe under 10 (my guess). It runs locally on the same computer and you may run client remotely if you want to share workstation resources with other people (they may use low end laptops).

Stefan

---

### Post by kaspar_silas on 2011-07-22
Well after two email requests and two long waits with bugger all response I think I can officially say this was somewhat of a waste of time. 

Pity but oh well.

---

### Post by Stefanbanev on 2011-07-22
> **kaspar_silas said:**
> Well after two email requests and two long waits with bugger all response I think I can officially say this was somewhat of a waste of time. 

Pity but oh well.

Does not it work under ubuntu or you just could not get the license?

They are very selective, I heard it the second time. I associate with them so I did not have such experience besides they were very persistent to make me get the recommended hardware.

Stefan

---

### Post by kaspar_silas on 2011-07-23
I am sure it would work fine under ubuntu, thou as I mentioned earlier whatever the necessary distro and hardware it is not really much of an issue. The problem was they just never replied. 

Their website says they will check "to determine your eligibility for a research-only license". I assumed when I submitted they were just checking I was a real researcher. If they are being selective then I guess they are after collaboration with those of similar interests or maybe the commercial folk. Naturally that is totally fine but that is not what the website or a "research-only license" implies, to me anyway. 

In either case an email explaining the above or just saying "no" would have been nice. But maybe I am just being old and grumpy.

---

### Post by kaspar_silas on 2011-08-03
Okay an update (to be fair) they emailed back and had actually been considering the application.

So I was just being grumpy. Apologies to FOVIA.

EDIT: FOVIA actually turned out to be amazingly helpful and I would recommend them entirely.

---

