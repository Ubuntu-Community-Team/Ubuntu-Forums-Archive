---
title: "Email Notification Program"
date: 2009-05-07
forum: General Help
---

### Post by DBQ on 2009-05-07
Hi everybody.  I am looking for a simple email checking program (such as GMailNotifier).  Which can do the following:

* Run on Ubuntu (duh! ;)).

* Work with gmail

* Be simple - not be a full-fledged email client such as evolution or Thunderbird, just a checker (like GMailNotifier).

* Whenever email arrives show a notification

* Be able to do this: If an email is from a specific address then play a sound of choice or trigger some command.

Any suggestions?  Is the last requirement even possible with the current programs? Thank you all.

---

### Post by maheshasolkar on 2009-05-07
You could use one of these:

  [https://launchpad.net/gm-notify](https://launchpad.net/gm-notify)

  [https://launchpad.net/mail-notification](https://launchpad.net/mail-notification)


Depending on which one you like, use one of the following to install:

```
  sudo aptitude install gm-notify
  sudo aptitude install mail-notification
```

EDIT: For gm-notify, you will need to use the PPA at:

  [https://launchpad.net/~gm-notify-maintainers/+archive/ppa](https://launchpad.net/~gm-notify-maintainers/+archive/ppa)

Directions on how to use it are on that page

---

### Post by colau on 2009-05-07
> **maheshasolkar said:**
> You could use one of these:

  [https://launchpad.net/gm-notify](https://launchpad.net/gm-notify)

  [https://launchpad.net/mail-notification](https://launchpad.net/mail-notification)


Depending on which one you like, use one of the following to install:

```
  sudo aptitude install gm-notify
  sudo aptitude install mail-notification
```

EDIT: For gm-notify, you will need to use the PPA at:

  [https://launchpad.net/~gm-notify-maintainers/+archive/ppa](https://launchpad.net/~gm-notify-maintainers/+archive/ppa)

Directions on how to use it are on that page

Thanks.
I was also searching this.

---

### Post by mark2741 on 2009-05-07
I've been using GNail Notifier the past couple of days and it works well - love it in conjunction with Jaunty's new unified notifications feature as whenever I get an email a notification just appears for a few seconds.

I was kind of concerned about inputting my email password into the app at first, but so far no one has hijacked me yet : )

---

### Post by lensman3 on 2009-05-08
A program called biff.

biff = "BIFF"

        This command, which turns on asynchronous mail notification,
        was actually named after a dog at Berkeley.

            I can confirm the origin of biff, if you're interested.
            Biff was Heidi Stettner's dog, back when Heidi (and I, and
            Bill Joy) were all grad students at U.C. Berkeley and the
            early versions of BSD were being developed.   Biff was
            popular among the residents of Evans Hall, and was known
            for barking at the mailman, hence the name of the command.

        Confirmation courtesy of Eric Cooper, Carnegie Mellon University

---

### Post by 1jackjack on 2009-05-20
I prefer mail-notification to gm-notify, as i prefer to have a dedicated system tray icon displaying the number of unread emails. Also, you can mouse over the icon to view info about the emails to figure out if it's worth reading them...

You can also setup mail-notification to use the new Jaunty notifications. See my article: [http://www.ubooboo.net/zimPage.php?page=Mail-Notification](http://www.ubooboo.net/zimPage.php?page=Mail-Notification)

---

### Post by mike555 on 2009-05-20
I use " checkgmail " it works very good with Jaunty ...

---

