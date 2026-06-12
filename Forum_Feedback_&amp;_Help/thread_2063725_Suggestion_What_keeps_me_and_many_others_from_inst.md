---
title: "Suggestion: What keeps me and many others from installing Ubuntu"
date: 2012-09-27
forum: Forum Feedback &amp; Help
---

### Post by Inoki on 2012-09-27
This is a serious suggestion directed towards current and future releases of Ubuntu.

The things that keep me from installing Ubuntu are:

- frequent kernel updates that do more harm than good
- blacklisting of older hardware&#65279;

Most people have encountered that annoying habit of Ubuntu making things that used to work in a previous version not work anymore in a newer one. That is why this is an appeal (and shouldn't be, because a good OS should support ALL THE HARDWARE) to:

- release only properly tested kernel updates

or

- install something similar to mintupdate, that avoids kernel updates, which is the reason Mint is more stable than Ubuntu
- quit the habit of blacklisting older hardware

This is an issue that has been haunting (former) Ubuntu users since Ubuntu practically arrived I believe. Each time with each new release something worked and then it didn't. Each new update broke something.

Would someone finally listen to the community and be reasonable about this?

---

### Post by snowpine on 2012-09-27
If you wish to skip kernel updates then use:

```
sudo apt-get upgrade
```

instead of:

```
sudo apt-get dist-upgrade
```

If you install a new kernel and it doesn't work, you can choose your old kernel in GRUB.

If you think you found a bug, [report it]("https://help.ubuntu.com/community/ReportingBugs").

---

### Post by Inoki on 2012-09-27
That's not exactly the type of answer I expected.

Ubuntu's aim is, after seeing all the vids and stuff, to be the most user friendly OS there is, am I right? In that case users should be able to skip all that hassle with codes and use terminal to the minimum extent possible, so a proper updater should be installed.

If the devs won't come up with a proper solution the distro will always remain the same and users will always have the same issues and many of them won't install it because of the same reason - its update system isn't simply measured.

Take Mint for example. Why has it surpassed Ubuntu? I will tell you.

For the past two years I've been using Mint for one reason only, mintupdate. It saved my system from crashes, avoiding those nasty kernel updates and delivering only updates, that wouldn't do any harm to the system. And it's just "rebranded Ubuntu". Ain't it funny when something based on Ubuntu is better than Ubuntu?

Bear in mind, that **NOT ONLY GEEKS AND HACKERS** use it!

That is why it should be as much user friendly as possible.

Wanna hack? Be a geek? Use Arch! Or something similar. Let the other, casual users not worry about their system and give them the ability and comfort to use it freely.

---

### Post by snowpine on 2012-09-27
> **Anathaen said:**
> That's not exactly the type of answer I expected.


If the new kernel doesn't work, then pick the old kernel from GRUB.

It's a simple, practical type of answer that even a beginner can follow. 

You like Mint's updater, I like to use 'apt-get' in the terminal, so I approach your question the way I would solve it myself, you choose the method that works best for you 2 years, everyone is happy! :)

---

### Post by Inoki on 2012-09-27
That's the typical answer of those who don't even want to consider other options for the improvement of the project and the satisfaction of many.

If the devs of Ubuntu have the same approach as yours, they can only long for users to install it, no matter what fancy things they add into it, it'll remain the same.

It'll crash systems and hardware will be blacklisted and a supreme operating system should support everything, to the last bit.

If Windows can do it, some other Linux distros also, why not Ubuntu?

And for the record, I dumped even Mint, because it adopts every single thing from Ubuntu, what used to work for me in a previous version didn't in a newer one.

---

### Post by snowpine on 2012-09-27
> **Anathaen said:**
> That's the typical answer of those who don't even want to consider other options for the improvement of the project and the satisfaction of many.

I am not an Ubuntu dev, I am just random internet guy, so please don't think my views represent those of UbuntuCorp. They are not reading this forum, so I gave you the link above if you want to communicate your bug directly to them. Another site you can share your ideas is [Ubuntu brainstorm]("http://brainstorm.ubuntu.com"). Are you willing to make the small effort to actually improve Ubuntu?

To be honest, I don't use Ubuntu, you apparently don't use Ubuntu either, and you haven't described what the actual hardware/kernel problem is, so I'm not sure why we're having this conversation. :)

---

### Post by Inoki on 2012-09-27
I was using Ubuntu. **WAS**. Looking at how they work on it I'd seriously give it a try if they'd be willing to make it more user friendly from another perspective, the real user perspective.

Coz quite frankly, a 50 years old user will not be willing to type something in a terminal, would they?

---

### Post by snowpine on 2012-09-27
You misunderstand my intentions.

Just because I give you an easy answer to your question using a 1-line command you can type in the terminal doesn't mean *you* have to do it that way. Ubuntu also gives you GUI point-and-click tools for updates and configuration, you can use those tools if you prefer. I only give you terminal commands because that's how I would do it myself, and I am trying to help you. Or do you not want to be helped, maybe you just want to vent, that is OK too. :)

---

### Post by Futant on 2012-09-27
> **Anathaen said:**
>  Coz quite frankly, a 50 years old user will not be willing to type something in a terminal, would they?

 You might be underestimating your elders...

---

### Post by Inoki on 2012-09-27
My intentions are solely for the good of the majority. Usability, simplicity are the keys.

Less is always more. Less in clicks in this matter.

Ubuntu devs should be aware of that.

But more to the point, blacklisting of older and troublesome hardware is a real issue here. That needs the highest attention, so that Ubuntu runs on every computer.

---

### Post by ajgreeny on 2012-09-27
> **Anathaen said:**
> I was using Ubuntu. **WAS**. Looking at how they work on it I'd seriously give it a try if they'd be willing to make it more user friendly from another perspective, the real user perspective.

[COLOR=Red]Coz quite frankly, a 50 years old user will not be willing to type something in a terminal, would they?[/COLOR]
Why ever not???

You make it sound as if 50 year old users are almost in the grave, can not possibly make use of a terminal with some simple commands, and are stupid idiots!

Have you considered that some users, some considerably older than 50, such as me, are quite able, and like to use the terminal for many purposes.  Many of us are also probably able to remember the "good old days" of ms-dos and its terminal commands, as I certainly can, though that was a lot less useful than the Linux terminal commands available to us now.

---

### Post by snowpine on 2012-09-27
> **Anathaen said:**
> Ubuntu devs should be aware of that.

But more to the point, blacklisting of older and troublesome hardware is a real issue here. That needs the highest attention, so that Ubuntu runs on every computer.

That would require that ordinary users such as yourself submit bug reports and brainstorms so that Ubuntu is tested on the widest possible range of hardware. Will you do this?

---

### Post by Inoki on 2012-09-27
> **snowpine said:**
> That would require that ordinary users such as yourself submit bug reports and brainstorms so that Ubuntu is tested on the widest possible range of hardware. Will you do this?

I'm curious how the folks over MS do it. Coz Windows may be pure crap, but at least it can run on anything.

---

### Post by Inoki on 2012-09-27
> **ajgreeny said:**
> Why ever not???

You make it sound as if 50 year old users are almost in the grave, can not possibly make use of a terminal with some simple commands, and are stupid idiots!

Have you considered that some users, some considerably older than 50, such as me, are quite able, and like to use the terminal for many purposes.  Many of us are also probably able to remember the "good old days" of ms-dos and its terminal commands, as I certainly can, though that was a lot less useful than the Linux terminal commands available to us now.

Am talking about the majority. Not many folks over 50 let's say, was just an example, simply put, elderly people won't be willling to type something into a terminal to install / update something.

That's the principle of Windows and that's why still many prefer Windows over anything.

It should be in the interest of the developers to make an OS as much user friendly as possible.

---

### Post by snowpine on 2012-09-27
> **Anathaen said:**
> Am talking about the majority. Not many folks over 50 let's say, was just an example, simply put, elderly people won't be willling to type something into a terminal to install / update something.


You do *not* have to use a terminal just to install/update something in Ubuntu! That's just false! I am regretting that I mentioned a terminal command earlier in this thread (I was only trying to help).

> **Anathaen said:**
> That's the principle of Windows and that's why still many prefer Windows over anything.

Windows has a terminal, same as Ubuntu. I really do not think that is the main reason why Windows has larger market share.

> **Anathaen said:**
> It should be in the interest of the developers to make an OS as much user friendly as possible.

"User friendly" to who? You are not an Ubuntu user, neither am I, so why should Ubuntu listen to our definition of "user friendly"?

---

### Post by Inoki on 2012-09-27
I was and you know what my first experience with Ubuntu was? It crashed my system after the first update.

That's what I'm trying to point out.

- no destructive kernel updates
- no blacklisting of older hardware

That's the whole point of this thread.

---

### Post by snowpine on 2012-09-27
> **Anathaen said:**
> I was and you know what my first experience with Ubuntu was? It crashed my system after the first update.

That's what I'm trying to point out.

- no destructive kernel updates
- no blacklisting of older hardware

That's the whole point of this thread.

And do you feel that, by making this thread, you have communicated enough information to solve the problem, to the people with the power to do so?

---

### Post by pqwoerituytrueiwoq on 2012-09-27
to anyone saying MS supports all hardware, they don't actually support it the manufactures support windows, not the other way around
not all manufacturers support linux and a lot of hardware is community supported and in some cases this is better than the manufactures Linux drivers

---

### Post by Iowan on 2012-09-27
Closed - this is not a forum/website problem.
> Forum Feedback & Help Report technical problems with the website here (i.e. broken features), or ask questions pertaining to forum features.

---

### Post by oldos2er on 2012-09-27
> **Anathaen said:**
> Coz quite frankly, a 50 years old user will not be willing to type something in a terminal, would they?

Lol.

---

### Post by lisati on 2012-09-27
> **oldos2er said:**
> Lol.

Ditto.

---

