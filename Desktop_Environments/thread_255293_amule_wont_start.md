---
title: "amule wont start"
date: 2006-09-11
forum: Desktop Environments
---

### Post by jabb on 2006-09-11
Hi all new to the forum so if this is the wrong place for my question im sorry :)

I was trying to install amule via apt-get, but after that I cant run the aplication

this is the error I get

 aMule Version: aMule 2.1.0 using wxGTK2 v2.6.1 (Unicoded)

Terminated after throwing an instance of 'CInvalidStateEx'
        what(): CRunTimeException::CInvalidStateException: CFile: Cannot get length of closed file.
        backtrace:
[2] wxThreadHelperThread::~wxThreadHelperThread() in amule [0x8081acc]
[3] wxEntry(int&, wchar_t**) in /usr/lib/libwx_baseu-2.6.so.0[0xb769da8d]
[4] wxEntry(int&, char**) in /usr/lib/libwx_baseu-2.6.so.0[0xb769daf8]
[5] CryptoPP::IteratedHashBase2<unsigned int, CryptoPP::EnumToType<CryptoPP::ByteOrder, 0>, CryptoPP::HashTransformation>::~IteratedHashBase2() in amule [0x81276cc]
[6] __libc_start_main in /lib/tls/i686/cmov/libc.so.6[0xb7411ea2]
[7] __gxx_personality_v0 in amule[0x807dad1]

Aborted


before that I installed at newer wxGTK2.7 from the site
[http://wxwidgets.org/downloads/](http://wxwidgets.org/downloads/)
using this:
deb [http://apt.tt-solutions.com/ubuntu/](http://apt.tt-solutions.com/ubuntu/) dapper main

so I thougt that I would have the appropriate widget then.
though from the error it seems to me that the problem is perhaps the newer version of widget I installed ?

I also tried a complete uninstall 
apt-get remove --purge amule
and then reinstalling it

this is what I have in repository

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://apt.tt-solutions.com/ubuntu/](http://apt.tt-solutions.com/ubuntu/) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

maybe I need to edit something there?

also I did try to compile amule myself, but running the ./configure I needed a never version of wxGtk.

what I would like to be albe to do is to complerely remove everything about amule so I can make a clean start again.
the first couple of times i did apt-get install amule it run fine, though I had problems with permission with were I choosed the temp and incomming directory

maybee I should make a new repository list and see if that helps?

anyway I hope someone is able to help me with this. thanks in advance.

---

