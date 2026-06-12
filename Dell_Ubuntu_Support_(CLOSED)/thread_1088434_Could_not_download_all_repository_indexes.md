---
title: "Could not download all repository indexes"
date: 2009-03-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zander1013 on 2009-03-06
hi,

i am trying to update my mini 9 run by hardy. but i get the message that is the title of this thread

Could not download all repository indexes 

and it lists these...

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-proposed/universe/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-proposed/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-proposed/multiverse/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-proposed/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-proposed/restricted/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-proposed/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead.

:D

it IS connected to the internet. i am using it to post this thread.

please advise.

zander

---

### Post by Kevbert on 2009-03-06
It may be that work is being done on that particular server. You can wait a while and try later or choose a different server under System-Administration-Software sources.

---

### Post by sumit.kalra999 on 2009-03-06
Hi,
Don't take tension.
Sometimes the expire repositeries are removed from the server but on webspace, you find the link of expired repository and try to find them creates the error messages,

---

### Post by zander1013 on 2009-03-07
it is still giving this error. it gives it every time i try to run an update.

/etc/apt/sources* has only deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free in it.

what are the alternative sources i could use?

please advise.

thank you,

zander

---

### Post by ugm6hr on 2009-03-08
Is this a default Dell Mini 9 Ubuntu installation, or a manual one?

If the former, your sources are messed up; the standard Canonical repos do not have lpia packages.

If the latter, you have lpia specified - which doesn't exist.

Someone (presumably you) has modified the /etc/apt/sources.list file incorrectly - you need to sort it out.

If you have the default Dell Mini Ubuntu, the file should look like:

```
deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted

#PPA for OO.org3.0
#deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
#deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
```

PS: The final # entry is for OO.org 3.0 (it is deactivated by the #, so will not be available)

---

### Post by zander1013 on 2009-03-10
hi,

i have a oem install of ubuntu on the mini9.

if i replace the contents of /etc/apt/sources.list with the default given above will it synchronize the Software Sources tool to reflect the changes in the file?

i have only changed the sources.list file through the Software Sources tool so-far.

thank you,

zander

---

### Post by sirebral on 2009-03-10
Highly unlikely Zander.

The reason you are not able to connect to the repos that you are attempting to connect to is because canonical does not have LPIA structures there.  It seems only partners do.

To get rid of the error uncheck the boxes on your first tab in Software Sources, then try an update again.

EDIT: For more info.

Go here: [http://security.ubuntu.com/ubuntu/dists/hardy/main/](http://security.ubuntu.com/ubuntu/dists/hardy/main/)
Do you see an LPIA there?  Nope. i386, x64, yes. LPIA? Nope.

Go here: [http://archive.canonical.com/ubuntu/dists/hardy/partner/](http://archive.canonical.com/ubuntu/dists/hardy/partner/)
See the LPIA? Yes.  But it is in the /partner/ folder.  Remember that LPIA is a section of Intel research.

---

### Post by ugm6hr on 2009-03-11
> **zander1013 said:**
> if i replace the contents of /etc/apt/sources.list with the default given above will it synchronize the Software Sources tool to reflect the changes in the file?

Yes.

You can change it all back with Software Sources if you prefer, but I think a cut and paste using Text Editor (gedit) would be quicker and faster.

```
gksudo gedit /etc/apt/sources.list
```

Once done:

```
sudo apt-get update
```

I would suggest avoiding messing around with system settings unless you understand what you are doing.

@Sirebral: I am uncertain what you are saying here - but everything will work fine once sources.list is returned to point to the Dell / Canonical repository.

---

### Post by 123forman on 2009-08-17
I had a similar problem with my hp mini. In particular, i want to download some basic software that doesn't appear in HP's repositories, but I don't want to have to worry about dependencies etc. Is there some work-around? Some way to get non-lpia repositories?

---

### Post by ugm6hr on 2009-08-17
> **123forman said:**
> I had a similar problem with my hp mini. In particular, i want to download some basic software that doesn't appear in HP's repositories, but I don't want to have to worry about dependencies etc. Is there some work-around? Some way to get non-lpia repositories?

Give more details.

Which version on Ubuntu?

Which software?

In general - no.  lpia architecture requires lpia repositories.  However, you can manually convert packages to i386, or install them with GDebi.  apt-get / synaptic / Add&Remove will error though.

PS: You should start a new thread unless your problem is identical.  You will get better help.

---

### Post by HonzaPokorny on 2009-12-12
I seem to have the same problem. I'm using Ubuntu Karmic and I get the same error when hitting the Reload button in Synaptic. 

I tried to copy and paste the links into Firefox and the file downloaded no problems. Also, my wife's laptop (Ubuntu Karmic) has the same repositories set up and it updates fine. 

Any thoughts?

Thanks!

---

