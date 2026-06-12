---
title: "Making Prism use one profile? Possible?"
date: 2009-03-02
forum: General Help
---

### Post by inspired on 2009-03-02
Hi folks,
I recently installed Prism 0.9.1 using synaptic. I also installed a number of prism applications (gmail, google docs, etc.).

I want to install Gears. I know how to install it, but I have no discovered the Prism has a completely separate profile for every app I installed, which means I have to install Gears (and any other extensions) multiple times... into each prism app.

Is there any way to make Prism use the same profile (and therefore the same extensions, etc.) for all instances... for all apps?

I have about 8 prism apps now, and don't like the prospect of having to open each one and install the same extension into each one every time I want to add an extension.

Any help is gratefully appreciated.

Prism rocks! :guitar:

Jonathan

---

### Post by InspiredIndividual on 2009-03-04
Hello (partial) namesake! I'm not very experienced with Prism, but if the profiles are identical, you can use softlinks to ensure you need to change your profile only once. Create a single profile and replace all other profiles with a softlink. It might be best to place your profile somewhere different, so it won't end up being accidentally deleted upon removal of a specific application. I don't know if that could happen, just to be safe.

I'll illustrate what I mean with an example. Say, you've got applications appA, appB and appC with profile file prA, prB and prC. We want prA, prB and prC to stay the same. Say our prA is the profile as we want it. First, copy prA to your home directory, let's name it 'superprofile'. Afterwards, move prA, prB and prC to another directory. Anywhere will do, it's just for safekeeping. You can delete them after you've tested everything works as it should.

Finally, for each profile, create a link to our superprofile:

```
 ln -s /home/user/superprofile /way/to/oldDirectoryA/prA
```

Replace /way/to/oldDirectoryA/prA with the location prA was located before we moved it. Now, any time you change your profile in one of the applications, you actually change 'superprofile'. Therefor, the changes will apply to all applications.

I don't know how exactly Prism stores its profiles, so it's possible you'll need to tweak a bit. For example, if Prism uses multiple profile folders for each application instead of a single file, you'll need to link to each folder. If extensions are in one profile folder and application specific  settings in a different one, you'll need to link to the extensions profile folder only. If you need more specific advice, you'll need to elaborate a bit on the way the Prism profiles are stored.

---

