---
title: "Fedora Core-6"
date: 2006-10-22
forum: Fedora/RedHat and derivatives
---

### Post by sherlock-holmes on 2006-10-22
we have several discussions comparing ubuntu and windows...
how about fedora core-6. Its coming out on oct 24  and edgy on oct 26th.. they sy FC6 will be ultra stable (several reports on this) and good  printing configuration, wi-fi artwork etc...what say?

i am runnung on edgy and there are several things that are broken. X doesnt work.. i have tried everything except a clean install (so many files to back up) ... FC6 comes with latest kernel etc...

i am going to try FC6 on the laptop this time... may be even make a shift.. with my office pc running on edgy..

thoughts?

---

### Post by chaosgeisterchen on 2006-10-22
Fedora suffers from using RPM. Everything else is fine with them, as they are a major force in the Linux universe.

---

### Post by plb on 2006-10-22
Never tried Fedora, Last I used Redhat however was version 6. Never really heard anything bad about the distro.

---

### Post by Lord Illidan on 2006-10-22
Try it out, tell us what you think.. always try out major distros.

---

### Post by chaosgeisterchen on 2006-10-22
This will be the week of major distros, as FC6 and Edgy are released. I wonder how they will both work. Fedora Core is a really insteresting distribution as it has great hardware detection (as far as I heard) and a large community which is not a bit behind the ours.

But, well, Ubuntu is somewhat bigger than Fedora.

---

### Post by ComplexNumber on 2006-10-22
> **chaosgeisterchen said:**
> Fedora suffers from using RPM. Everything else is fine with them, as they are a major force in the Linux universe.
it doesn't *suffer* from rpm at all. thats just ignorant. 

i'm running fedora 5 at the moment, and its the only distro(out of opensuse 10, SLED 10, ubuntu, mepis 6.0) which allows me to access the repos via broadband. none of the others did, even though i could connect to the web via firefox ok. i'll be upgrading to fedora 6 when its released.

---

### Post by chaosgeisterchen on 2006-10-22
I would certainly miss all those fine dpkg-tools while using Fedora, that's all.

So, from my point of view, dpkg is the better tool to maintain a system.. but you should first tell me what Fedora has to offer in comparison, please.

---

### Post by plb on 2006-10-22
The one thing I noticed is you need several CDs just to install Fedora...

---

### Post by Kobalt on 2006-10-22
If I had to run away from Ubuntu, then I'd go towards Fedora I think... But I must agree with chaosgeisterchen, I can't think of anything good enough to replace tools like Aptitude. Yast from SUSE used to be a good tool, but it's getting heavier and heavier... 
I must give credit to Fedora on their artwork though, it has always been polished and well tuned I think.

---

### Post by ComplexNumber on 2006-10-22
> **chaosgeisterchen said:**
> I would certainly miss all those fine dpkg-tools while using Fedora, that's all.

So, from my point of view, dpkg is the better tool to maintain a system.. but you should first tell me what Fedora has to offer in comparison, please.
what fine dpkg tools are these? :lol:. maybe you've never used rpm properly. i don't knw. i found dpkg to be crippled compared to rpm, and rpm gives far more options. here is a printout of "rpm --help":

Usage: rpm [OPTION...]

Query options (with -q or --query):
  -c, --configfiles                list all configuration files
  -d, --docfiles                   list all documentation files
  --dump                           dump basic file information
  -l, --list                       list files in package
  --queryformat=QUERYFORMAT        use the following query format
  -s, --state                      display the states of the listed files
  -a, --all                        query/verify all packages
  -f, --file                       query/verify package(s) owning file
  -g, --group                      query/verify package(s) in group
  -p, --package                    query/verify a package file
  -W, --ftswalk                    query/verify package(s) from TOP file tree
                                   walk
  --pkgid                          query/verify package(s) with package
                                   identifier
  --hdrid                          query/verify package(s) with header
                                   identifier
  --fileid                         query/verify package(s) with file identifier
  --specfile                       query a spec file
  --triggeredby                    query the package(s) triggered by the
                                   package
  --whatrequires                   query/verify the package(s) which require a
                                   dependency
  --whatprovides                   query/verify the package(s) which provide a
                                   dependency
  --nomanifest                     do not process non-package files as
                                   manifests

Verify options (with -V or --verify):
  --nomd5                          don't verify MD5 digest of files
  --nofiles                        don't verify files in package
  --nodeps                         don't verify package dependencies
  --noscript                       don't execute verify script(s)
  -a, --all                        query/verify all packages
  -f, --file                       query/verify package(s) owning file
  -g, --group                      query/verify package(s) in group
  -p, --package                    query/verify a package file
  -W, --ftswalk                    query/verify package(s) from TOP file tree
                                   walk
  --pkgid                          query/verify package(s) with package
                                   identifier
  --hdrid                          query/verify package(s) with header
                                   identifier
  --fileid                         query/verify package(s) with file identifier
  --specfile                       query a spec file
  --triggeredby                    query the package(s) triggered by the
                                   package
  --whatrequires                   query/verify the package(s) which require a
                                   dependency
  --whatprovides                   query/verify the package(s) which provide a
                                   dependency
  --nomanifest                     do not process non-package files as
                                   manifests

File tree walk options (with --ftswalk):
  --comfollow                      FTS_COMFOLLOW: follow command line symlinks
  --logical                        FTS_LOGICAL: logical walk
  --nochdir                        FTS_NOCHDIR: don't change directories
  --nostat                         FTS_NOSTAT: don't get stat info
  --physical                       FTS_PHYSICAL: physical walk
  --seedot                         FTS_SEEDOT: return dot and dot-dot
  --xdev                           FTS_XDEV: don't cross devices
  --whiteout                       FTS_WHITEOUT: return whiteout information

Signature options:
  --addsign                        sign package(s) (identical to --resign)
  -K, --checksig                   verify package signature(s)
  --delsign                        delete package signatures
  --import                         import an armored public key
  --resign                         sign package(s) (identical to --addsign)
  --nodigest                       don't verify package digest(s)
  --nosignature                    don't verify package signature(s)

Database options:
  --initdb                         initialize database
  --rebuilddb                      rebuild database inverted lists from
                                   installed package headers

Install/Upgrade/Erase options:
  --aid                            add suggested packages to transaction
  --allfiles                       install all files, even configurations
                                   which might otherwise be skipped
  --allmatches                     remove all packages which match <package>
                                   (normally an error is generated if
                                   <package> specified multiple packages)
  --badreloc                       relocate files in non-relocatable package
  -e, --erase=<package>+           erase (uninstall) package
  --excludedocs                    do not install documentation
  --excludepath=<path>             skip files with leading component <path>
  --fileconflicts                  detect file conflicts between packages
  --force                          short hand for --replacepkgs --replacefiles
  -F, --freshen=<packagefile>+     upgrade package(s) if already installed
  -h, --hash                       print hash marks as package installs (good
                                   with -v)
  --ignorearch                     don't verify package architecture
  --ignoreos                       don't verify package operating system
  --ignoresize                     don't check disk space before installing
  -i, --install                    install package(s)
  --justdb                         update the database, but do not modify the
                                   filesystem
  --nodeps                         do not verify package dependencies
  --nomd5                          don't verify MD5 digest of files
  --nocontexts                     don't install file security contexts
  --noorder                        do not reorder package installation to
                                   satisfy dependencies
  --nosuggest                      do not suggest missing dependency
                                   resolution(s)
  --noscripts                      do not execute package scriptlet(s)
  --notriggers                     do not execute any scriptlet(s) triggered
                                   by this package
  --oldpackage                     upgrade to an old version of the package
                                   (--force on upgrades does this
                                   automatically)
  --percent                        print percentages as package installs
  --prefix=<dir>                   relocate the package to <dir>, if
                                   relocatable
  --relocate=<old>=<new>           relocate files from path <old> to <new>
  --repackage                      save erased package files by repackaging
  --replacefiles                   ignore file conflicts between packages
  --replacepkgs                    reinstall if the package is already present
  --test                           don't install, but tell if it would work or
                                   not
  -U, --upgrade=<packagefile>+     upgrade package(s)

Common options for all rpm modes and executables:
  -D, --define='MACRO EXPR'        define MACRO with value EXPR
  -E, --eval='EXPR'                print macro expansion of EXPR
  --macros=<FILE:...>              read <FILE:...> instead of default file(s)
  --nodigest                       don't verify package digest(s)
  --nosignature                    don't verify package signature(s)
  --rcfile=<FILE:...>              read <FILE:...> instead of default file(s)
  -r, --root=ROOT                  use ROOT as top level directory (default:
                                   "/")
  --querytags                      display known query tags
  --showrc                         display final rpmrc and macro configuration
  --quiet                          provide less detailed output
  -v, --verbose                    provide more detailed output
  --version                        print the version of rpm being used

Options implemented via popt alias/exec:
  --scripts                        list install/erase scriptlets from
                                   package(s)
  --setperms                       set permissions of files in a package
  --setugids                       set user/group ownership of files in a
                                   package
  --conflicts                      list capabilities this package conflicts
                                   with
  --obsoletes                      list other packages removed by installing
                                   this package
  --provides                       list capabilities that this package provides
  --requires                       list capabilities required by package(s)
  --info                           list descriptive information from package(s)
  --changelog                      list change logs for this package
  --xml                            list metadata in xml
  --triggers                       list trigger scriptlets from package(s)
  --last                           list package(s) by install time, most
                                   recent first
  --filesbypkg                     list all files from each package
  --fileclass                      list file names with classes
  --filecolor                      list file names with colors
  --filecontext                    list file names with security context from
                                   header
  --fscontext                      list file names with security context from
                                   file system
  --recontext                      list file names with security context from
                                   policy RE
  --fileprovide                    list file names with provides
  --filerequire                    list file names with requires
  --redhatprovides                 find package name that contains a provided
                                   capability (needs rpmdb-redhat package
                                   installed)
  --redhatrequires                 find package name that contains a required
                                   capability (needs rpmdb-redhat package
                                   installed)
  --buildpolicy=<policy>           set buildroot <policy> (e.g. compress man
                                   pages)
  --with=<option>                  enable configure <option> for build
  --without=<option>               disable configure <option> for build

Help options:
  -?, --help                       Show this help message
  --usage                          Display brief usage message

---

### Post by plb on 2006-10-22
Shots are now up at osdir of FC6

[http://shots.osdir.com/slideshows/slideshow.php?release=749&slide=23&title=fedora+core+6+screenshots](http://shots.osdir.com/slideshows/slideshow.php?release=749&slide=23&title=fedora+core+6+screenshots)

---

### Post by chaosgeisterchen on 2006-10-22
I must cut out apt-options as they also work with any other distribution.

I find things like dpkg-reconfigure and dpkg-divert very interesting, the packet managing system is very good I have to say. You can fix fundamental problems very fast (in most cases).

//edit

concerning the shots:

Awesome artwork! And cool installer as well.

They took the infinity-logo and merged it with some DNA-theme. I do not like the icons but that's subjective. Well done I would like to say. I am probably testing it - dude, they really use 2.6.18. Does this have any positive effect?

---

### Post by Lord Illidan on 2006-10-22
looks better than FC 5. Wallpaper now looks more serious, and the theme is less shiny.

---

### Post by Burgresso on 2006-10-22
I've tried both Fedora 4 and 5, but not 6. 5 was ultra-polished and sassy. They were ok but had a key piont of failure for me. 

Despite using one of the most common wireless cards (non USB, even) in the universe - both versions did not support them out of the box. I tried forever to get it to work. I could not believe it, expecially when this was not fixed in FC5. Ubuntu since (at least)  5.10 has supported it out of the box with no set-up. The Fedora forums are filled with requests about how to get this wireless card to work.

I know I'm over generallizing and assuming that making a distro is a bit easier then it probably is, but couldn't they look to see how Ubuntu did it?

I hope FC6 fixed this, but I would bet money otherwise. If they did, I would give it serious consideration as my desktop. I'll try it and see.

---

### Post by AndyCooll on 2006-10-22
Just thought it worth pointing out that there are actually quite a few threads in these forums discussing Fedora Core, and in turn comparing it to Ubuntu. Indeed the distro even has its own section! Here: [Other OS Talk - Red Hat/Fedora]("http://www.ubuntuforums.org/forumdisplay.php?f=162")

Ubuntu Forums > Community Discussions  > Categories  > Other OS Talk > RedHat/Fedora

:cool:

---

### Post by BWF89 on 2006-10-22
Could anyone tell me how Fedora Core 6 compares to Scientific Linux 4.4?

---

### Post by SpEcIeS on 2006-10-23
Well I really liked **RPM** and I also like *dpkg* tools too. **RPM** is really easy to use and building packages is very easy. **[COLOR="Red"]DEB[/COLOR]** packages on the other had are a little more tedious.

---

### Post by ComplexNumber on 2006-10-24
here's a screenshot of my desktop showing the the icons destined for FC7. they are called Echo.

---

### Post by LMP900 on 2006-10-24
Why are there three FC6 threads? So confusing ;) Anyways,

> **ComplexNumber said:**
> here's a screenshot of my desktop showing the the icons destined for FC7. they are called Echo.

Echo looks good, although I really like their current folder icons. I know they've been using them for quite some time, but those folder icons are simple and attractive. The other icons look good, however.

One thing they really need to change is the "Reload" or "Refresh" icon. Ubuntu probably has the most attractive icon (the blue circle-arrow) out of any OS, including Vista and OS X.

---

### Post by sherlock-holmes on 2006-10-24
I am right now downloading FC6. I will update here my experience. 
People are crazy on that, that the downloading take a looooong time...dejavu on the ubuntu LTS download.

@ major distros releasing the stable version in the span of a couple of days is creating a lot of buzz in the community...

I see that the hits are running a little low on ubuntu--- last seven days i mean (according to distrowatch)....

for 7 days...
1  	Ubuntu  	2839 (down)
2 	openSUSE 	2415 (down)
3 	Fedora 	        1983  (up)

still ubuntu leads FC by almost 1000 hits..

it would be interesting to see how it goes in the coming weeks...!!!

---

### Post by ComplexNumber on 2006-10-24
> Echo looks good, although I really like their current folder icons.
you mean these bluecurve icons? :p

---

### Post by chaosgeisterchen on 2006-10-24
> **sherlock-holmes said:**
> 
for 7 days...
1  	Ubuntu  	2839 (down)
2 	openSUSE 	2415 (down)
3 	Fedora 	        1983  (up)

still ubuntu leads FC by almost 1000 hits..

it would be interesting to see how it goes in the coming weeks...!!!

SuSE will drop and both Ubuntu and Fedora rise as they both are releasing their new versions this week.

---

### Post by SpEcIeS on 2006-10-24
> **chaosgeisterchen said:**
> SuSE will drop and both Ubuntu and Fedora rise as they both are releasing their new versions this week.
I concur. ;)

---

### Post by LMP900 on 2006-10-24
> **ComplexNumber said:**
> you mean these bluecurve icons? :p

Yes! The only folder icons that look better than those are Vista's.

The bluecurve folder icons look simple and professional (no shiny :p), and they needed only a slight improvement; not a complete change.

---

