---
title: "Gimpshop Nightmare"
date: 2009-04-22
forum: General Help
---

### Post by omgseth on 2009-04-22
I cannot for the life of me install Gimpshop on my 8.10...

I tried installing the deb package with regular gimp already installed... didn't work... didn't even show up in my app menu... tried to remove old gimp and install Gimpshop... nope. Any help that you could give would be amazing. Tried to solve it myself but hasn't worked ( as much as I've googled I can't find the answer ).

---

### Post by omgseth on 2009-04-22
Tried the same stuff again like an idiot... gah! I'm determined!

---

### Post by joey-elijah on 2009-04-22
Well at least you're not lulled into a false sense of accomplishment like i usually was - it'd install fine... but Gimpshop would open up and look identical to regular gimp.. thus defeating the point...

Gimpshop is incredibly out dated now anyway. Whilst i still have to use Photoshop (just used to it) i have managed to do a few bits and bobs in regular gimp. I assume you're used to Photoshop and want a familiar interface etc

---

### Post by afrodeity on 2009-04-22
As far as I'm aware you have to totally remove Gimp as well as its dependencies like 

sudo apt-remove gimp gimp-data gimp-gnomevfs gimp-plugin-registry gimp-python libgimp2.0 ubuntu-desktop xsane

then install gimp.

which should then prompt for any dependencies.

I never got around to doing this since I found the idea of removing the ubuntu-desktop a bit nightmarish. So haven't done this, but nevetheless one of the former package maintainers assures me its totally safe. Go ahead and try and report back.:)

---

### Post by omgseth on 2009-04-22
> **joey-elijah said:**
> Well at least you're not lulled into a false sense of accomplishment like i usually was - it'd install fine... but Gimpshop would open up and look identical to regular gimp.. thus defeating the point...

Gimpshop is incredibly out dated now anyway. Whilst i still have to use Photoshop (just used to it) i have managed to do a few bits and bobs in regular gimp. I assume you're used to Photoshop and want a familiar interface etc

Yeah, I have a virtual machine with Photoshop in it, but it's such a pain to have to start up a vm, then open up Photoshop, then navigate to my shared folder... I mean it's not hard but... it's a bit of a pain.

---

### Post by omgseth on 2009-04-22
Thought I'd found a nice compromise, using Virtualbox in seamless mode, but there's problems there too. Photoshop is the devil, I'm convinced of it. Damn Adobe for not making it Linux friendly! It's not like no one uses it! I think I'm going to mope angrily for a moment, then try something else...

---

### Post by afrodeity on 2009-05-19
You could always remind Photoshop that [http://cnr.com](http://cnr.com) exists (click 'n run). Apparently commercial Linux software is available, and as far as I am concerned, if you purchased a licence for photoshop, they should give you an application to run on whatever platform.

---

