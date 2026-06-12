---
title: "generate list of programs automatically?"
date: 2009-01-22
forum: General Help
---

### Post by Bramkaandorp on 2009-01-22
Hi there,

Does anyone know a way to generate a list of programs, which I can print to paper afterwards? Because I am sick of gathering the info myself.

This is because I reinstall Ubuntu quite often, and want to install as fast as possible.

Thanks,

Bram

---

### Post by oldos2er on 2009-01-22
dpkg --get-selections > installed-software

---

### Post by Bramkaandorp on 2009-01-22
Although that is a great tool, I was actually talking about a command to get a list of the programs in the applications menu. The list I have from the command you gave is far too long, and contains way more than I need.

So thanks anyway, but I need something more specific.

Cheers,

Bram

---

### Post by 2hot6ft2 on 2009-01-22
> **Bramkaandorp said:**
> 
This is because I reinstall Ubuntu quite often, and want to install as fast as possible.
If the purpose is to make the reinstall fast and easy that's not too hard to do. And have everything installed like you do now.
> **handydan918 said:**
> Okay, this should be in the wiki, or something. It's so simple, yet so powerful.

```
sudo dpkg --get-selections
```

```
sudo dpkg --get-selections > softwarelist
```
At this point in the proceedings, you hose your system and reinstall, and then...

```
dpkg --set-selections < softwarelist
```

```
apt-get dselect-upgrade
```

Enjoy.
The list will be long. For one to print you'll have to shorten it but no need to print it if you just plan on reinstalling using the list.

I don't know of a way to just print the menu list

---

### Post by Bramkaandorp on 2009-01-22
Great! This is really what I was looking for. I can see the advantage over a simple list.

Thanks a lot.

Cheers,

Bram

---

