---
title: "Clean up my system? :)"
date: 2006-02-10
forum: Desktop Environments
---

### Post by monotux on 2006-02-10
Hello everyone!

I'm thinking of migrating to Dapper Drake, but I feel that I need to do some cleaning in my system first - there are a lot of custom installed packages and a lot of repositories that I don't know what they do... :(

And why do I think that?
I'll show you:
```
root@fabric:/home/oscar# apt-get install beagle
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  beagle: Depends: libevolution-cil (>= 0.10.1) but it is not going to be installed
          Depends: libgconf2.0-cil (< 2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed
          Depends: libglade2.0-cil (< 2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed
          Depends: libglib2.0-cil (< 2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed
          Depends: libgnome2.0-cil (< 2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed
          Depends: libgtk2.0-cil (< 2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed
          Depends: libevolution-cil but it is not going to be installed
E: Broken packages

```

...wtf? I have versions that are too recent? :confused:

This is why I need to clean up my system.
Is there any way of comparing my installed packages with those in the official repositories, remove invalid, downgrade libraries etc?
I'm not even sure where to begin any research in this :-(

Can anyone help me, please?

---

### Post by dcstar on 2006-02-10
[QUOTE=monotux]Hello everyone!

I'm thinking of migrating to Dapper Drake, but I feel that I need to do some cleaning in my system first - there are a lot of custom installed packages and a lot of repositories that I don't know what they do... :(
......
This is why I need to clean up my system.
Is there any way of comparing my installed packages with those in the official repositories, remove invalid, downgrade libraries etc?
I'm not even sure where to begin any research in this :-(

Can anyone help me, please?[/QUOTE]
Easiest way to do it may be to remove ALL unofficial repositories, then "Force Version" any "Local or Obsolete" packages to the current official versions.

---

