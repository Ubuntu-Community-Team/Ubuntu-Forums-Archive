---
title: "aMule upgrade"
date: 2006-07-28
forum: Desktop Environments
---

### Post by Exil on 2006-07-28
After struggling for a very long time I finally got High ID, although I'm not really sure how I did it.

Now my doubt is; how do I upgrade aMule to the newest version (I am currently running 2.1.0)? In windows I just downloaded the Binaries and smashed the old ones with only the necessary new ones. I found that if I used the installer eMule lost speed (as if I lost the earned credits), this way, that did not happen.

However, I do not know how to do this in Ubuntu, I have tried looking for updates through the Update Manager, but it does not find upgrades for aMule, still, when I start aMule it comes with a message saying that I am running an old version. Another question: if Update Manager had found an upgrade, would it smash my credits?

Any ideas?

---

### Post by mlind on 2006-07-28
Dapper's amule is version 2.1.0-1ubuntu1 and will stay so unless there's some security related update that needs to be applied :( 
I've built newer amule from [Debian unstable]("http://packages.debian.org/unstable/x11/amule"), feel free to install it if you want, but it's not official Ubuntu package.

Repository is
```

deb http://www.elisanet.fi/mlind/ubuntu dapper main

```

---

### Post by Exil on 2006-07-28
Thanx mlind :)
I'll save your link for now, as I am still too green on linux to do try out your version :)

---

### Post by MWAAAHAAA on 2006-07-28
In linux one either installs things per package manager, as you have probably done up until now, or alternatively one downloads the source code for the program and compiles it, e.g. if one requires a newer version of the program which is not yet available through the package manager. Binary installers are quite rare and I do not use them unless I absolutely have to, as with my ATI drivers, which are the only exception on my system.

---

### Post by yaztromo on 2006-07-31
> **mlind said:**
> Dapper's amule is version 2.1.0-1ubuntu1 and will stay so unless there's some security related update that needs to be applied :( 
I've built newer amule from [Debian unstable]("http://packages.debian.org/unstable/x11/amule"), feel free to install it if you want, but it's not official Ubuntu package.

Repository is
```

deb http://www.elisanet.fi/mlind/ubuntu dapper main

```

Thanks for this. Just used it to upgrade my amule from 2.1.0 to 2.1.3 and it worked fine.

---

### Post by stuart_75 on 2006-08-02
Does this newer version of amule support files larger than 4gb?

If so how do I download and install it, im very new to linux and have only used the add/remove program or package manager to install software.


Thanks

---

### Post by mlind on 2006-08-02
> **stuart_75 said:**
> Does this newer version of amule support files larger than 4gb?

If so how do I download and install it, im very new to linux and have only used the add/remove program or package manager to install software.


Thanks

After reading these, you should be able to add new repository and install this package.

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by stuart_75 on 2006-08-02
Thanks for the quick reply.
Ive used GDebi to install the latest version of amule but now I get an error saying "Error: Dependency is not satisfiable: amule-common"

Ive tried installing amule common then retrying the amule 2.1.3 but with no luck and the same error.

Any ideas?

---

### Post by yaztromo on 2006-08-02
> **stuart_75 said:**
> Does this newer version of amule support files larger than 4gb?

Not yet. It's planned for the next amule release I think.

---

### Post by stuart_75 on 2006-08-02
> **yaztromo said:**
> Not yet. It's planned for the next amule release I think.

Thanks,

Ive reinstalled the older version for now. I really need 4gb+ file support, otherwise ill go back to XP. Any news on when this feture will be released?

---

### Post by mlind on 2006-08-02
> **stuart_75 said:**
> Thanks,

Ive reinstalled the older version for now. I really need 4gb+ file support, otherwise ill go back to XP. Any news on when this feture will be released?

That feature is supposed to be implemented on amule's svn trunk. Download the daily snapshot and compile it yourself.

---

### Post by stuart_75 on 2006-08-02
> **mlind said:**
> That feature is supposed to be implemented on amule's svn trunk. Download the daily snapshot and compile it yourself.

For a noob like myself that is out of the question without a step by step walkthrough. :(

---

### Post by mlind on 2006-08-02
> **stuart_75 said:**
> For a noob like myself that is out of the question without a step by step walkthrough. :(

amule wiki contains steps required for doing a manual build [http://www.amule.org/wiki/index.php/Compilation_Installation](http://www.amule.org/wiki/index.php/Compilation_Installation)
Other than that, you'll have to wait until new version gets officially released.

---

### Post by yaztromo on 2006-08-03
Don't forget to install the package build-essential first.

---

