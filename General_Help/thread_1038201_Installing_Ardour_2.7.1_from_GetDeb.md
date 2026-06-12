---
title: "Installing Ardour 2.7.1 from GetDeb"
date: 2009-01-12
forum: General Help
---

### Post by ac_d600 on 2009-01-12
Using Ubunto 8.04

Hello,

I'm trying to install the latest version of Ardour(2.7.1) from Getdeb,
but I keep getting "Error:Dependency is not satisfiable: libasound2".
BUT.. I do have version Ardour 2.3 installed, from the Ubuntu repositories,
so I know for a fact that I do have libasound2 installed.. any ideas on
what the problem could be??

Thanks
Alan

---

### Post by adult swim on 2009-01-12
edit: im a dummy

---

### Post by mssever on 2009-01-12
> **ac_d600 said:**
> 
so I know for a fact that I do have libasound2 installed.. any ideas on
what the problem could be??
Do you know this because you checked that libasound2 was installed, or because you assumed that you had it with the previous version of ardour (such an assumption might not be valid)? Also, make sure that the version dependencies match. It's possible that the deb you're trying to install dependds on a different version of libasound2 than the one you have installed.

Also, ignore the advice to install the -dev package. If you needed libasound2-dev you would have gotten an error about that package. Usually, -dev packages are only for building from source.

---

### Post by adult swim on 2009-01-12
> **mssever said:**
> 
Also, ignore the advice to install the -dev package. If you needed libasound2-dev you would have gotten an error about that package. Usually, -dev packages are only for building from source.

instead of getdeb i thought he said sourceforge 
woops :D

---

### Post by ac_d600 on 2009-01-12
> **mssever said:**
> Do you know this because you checked that libasound2 was installed, or because you assumed that you had it with the previous version of ardour (such an assumption might not be valid)? Also, make sure that the version dependencies match. It's possible that the deb you're trying to install dependds on a different version of libasound2 than the one you have installed.

Also, ignore the advice to install the -dev package. If you needed libasound2-dev you would have gotten an error about that package. Usually, -dev packages are only for building from source.

I do have libasound 1.0.15-3ubuntu4 installed, according to Package Manager.. how do I check the dependencies
for the deb I downloaded?

Thanks
Alan

---

### Post by mssever on 2009-01-12
> **ac_d600 said:**
> I do have libasound 1.0.15-3ubuntu4 installed, according to Package Manager.. how do I check the dependencies
for the deb I downloaded?

Thanks
Alan
Hopefully running ```
less package_filename.deb
```will give you the information you need, though it's possible that that's not the default behavior of less.

---

### Post by adult swim on 2009-01-12
you need libasound2 (>> 1.0.17)
and thanks mssever i didnt know you could use less in such a way.

---

### Post by ac_d600 on 2009-01-12
So how would I get libasound2 1.0.17  in Hardy??

Thanhs
Alan

---

### Post by mssever on 2009-01-12
> **ac_d600 said:**
> So how would I get libasound2 1.0.17  in Hardy??

Thanhs
Alan
I'm guessing that'll be difficult. You can grab the deb from Intrepid or Debian and try to install it, but there's a good chance you'll face more dependency conflicts. If you push it far enough, you could end up with badly broken sound or worse.

A better approach, I think, would be to use pbuilder[1] to build ardour from a source package. There's a good chance you can avoid upgrading libasound2 that way. I like to grab source packages from Debian unstable, since they're usually the latest version.

[1] See [http://ubuntuforums.org/showthread.php?t=206382](http://ubuntuforums.org/showthread.php?t=206382)

---

### Post by ac_d600 on 2009-01-14
Thanks mssever for the help. I think I'll just continue using the Ardour version that I have.
I've only been using Ubuntu for about 4 months now and I'm happy with the way its working
so I don't want to mess anything up.. ;)

Thanks Again.

---

