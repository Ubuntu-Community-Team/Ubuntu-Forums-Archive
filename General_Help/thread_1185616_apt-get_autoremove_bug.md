---
title: "apt-get autoremove bug"
date: 2009-06-12
forum: General Help
---

### Post by change_mode on 2009-06-12
I recently removed Epiphany, because I don't need it, including the package with the epiphany debugging symbols.
Since that package was part of the meta package gnome-dbg, the meta package was also removed.
Now when I run autoremove, it tries to remove all the other debugging packages that were included in gnome-dbg, even though the importance of these packages obviously hasn't changed - only the metapackage is gone.

How can I fix this?

---

### Post by jimv on 2009-06-12
If you install those packages on their own, it will stop trying to remove them...so basically, run "sudo apt-get install --reinstall yourpackages"

---

### Post by aysiu on 2009-06-12
You don't even have to include the *--reinstall* parameter.

You can just explicitly install them (without) redownloading them, and it should be fine.

---

### Post by change_mode on 2009-06-13
There were way too many packages to install/reinstall them manually... I created an autoremove filter in Synaptic and reinstalled all those packages with no effect. They still showed up in autoremove.
I decided to delete them, not worth the trouble. Synaptic should ask the user if he wants to unlink the rest of the packages from the metapackage if a part of it is uninstalled.

Another question: Is there an easy way to remove all packages that come from a certain metapackage?

---

### Post by aysiu on 2009-06-13
You have to do it with *apt-get*, not Synaptic.

And you don't have to install them manually one at a time. You can just highlight the whole list and then paste it into the terminal: ```
sudo apt-get install package1 package2 package3 package4 etc
```

---

### Post by mc4man on 2009-06-13
IF you reach a point where there are packages listed for autoremove that you **know you want to keep **then this will 'remark' them (typically occurs by using an apt-get build-dep without a  automatic=false option
```

sudo aptitude unmarkauto --schedule-only '~i'
```

---

### Post by change_mode on 2009-06-13
Ok, thanks for the info.

---

### Post by unutbu on 2009-06-13
What does the "~i" mean?

---

### Post by mc4man on 2009-06-13
> What does the "~i" mean?

When I was setting up intrepid to build some apps using build-deps I happened to notice that they were all being marked immediately for auto remove. (apt was patched to do this starting in 8.10

I remember finding an aptitude users manual (or similarly named) online and in the course of several trial and errors "~i" made it work. As to what it means I have no idea. (the 'depth' of the manual and possible commands was staggering

I've since figured out the option for build-deps, if  beforehand I know I wish to keep, otherwise I'll do normally and use the above command if I decide later to keep them.

---

### Post by unutbu on 2009-06-13
Thanks for the explanation, mc4man.

Would you happen to know: Does 
```

sudo aptitude unmarkauto --schedule-only '~i'
```

and
```

sudo aptitude keep-all
```

do the same thing?

---

### Post by mc4man on 2009-06-13
I'll have to get some packages marked for auto remove and try (this all came up last fall)( my autoremove is empty

I believe i starting reading thru pages like this for a solution back then (other than manually marking

[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html#tableSearchTermQuickGuide](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html#tableSearchTermQuickGuide)

For anyone that builds and uses build-deps the option if you want to keep from autoremove 

Ex. mplayer
```
sudo apt-get build-dep mplayer -o APT::Get::Build-Dep-Automatic=false
```

---

### Post by mc4man on 2009-06-13
Here you go, (added build-deps for totem

Edit (I'm an idiot, didn't use your command, will re-edit in a moment
>  does...
sudo aptitude keep-all

do the same thing

Yes it does, sometimes things can be so simple. (though I did get some interesting reading on aptitude

---

### Post by aysiu on 2009-06-13
Just paste this command into the terminal: ```
sudo apt-get install texlive-base-bin-doc texlive-base texlive-fonts-recommended texlive-pstricks-doc libosp5 gnome-pkg-tools libgnome-desktop-dev libsp1c2 lmodern texlive-common sp jadetex texlive-pstricks texlive-base-bin openjade dvipdfmx prosper libexif-dev tipa sgmlspl texlive-latex-recommended-doc texlive-latex-base-doc libostyle1c2 pgf texlive-latex-recommended texlive-generic-recommended texlive-latex-base texlive-fonts-recommended-doc libsgmls-perl libeel2-dev latex-beamer docbook-utils docbook-dsssl latex-xcolor texlive-doc-base tex-common libexempi-dev liblaunchpad-integration-dev
```

---

