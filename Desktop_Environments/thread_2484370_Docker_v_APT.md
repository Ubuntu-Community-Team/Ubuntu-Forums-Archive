---
title: "Docker v APT"
date: 2023-02-24
forum: Desktop Environments
---

### Post by Geoff_Lane on 2023-02-24
There is a lot of enthusiasm for docker and appimages nowadays, I understand they are easier to pack and are more compatible but am wondering; is it still advantageous to install using apt is one has the option for various installation methods?

I do understand the compatibility advantage as I do have some appimages on my system and on my multiboot system I can use same images on my arch and debian systems.

Geoff

---

### Post by DuckHook on 2023-02-24
You're raising a fraught topic that has generated heated debate on these and other forums. Rather than repeating it all, I've linked to another chat thread that explores it in some detail, with both sides of the debate well represented. Though the thread deals specifically with snap, most of the contents can be generalized to AppImage and FlatPak: [https://ubuntuforums.org/showthread.php?t=2481994](https://ubuntuforums.org/showthread.php?t=2481994)

I posted a number of observations but the most relevant to your question was probably the following:
[https://ubuntuforums.org/showthread.php?t=2481994&page=3&p=14130940#post14130940](https://ubuntuforums.org/showthread.php?t=2481994&page=3&p=14130940#post14130940)

There's a large and critical distinction between containers like Docker (and LXD which I use) versus packaging systems like Snapcraft, FlatPak & AppImage. The former are like VMs in that they offer an independent OS instance that we then populate with whatever we like from the repos. The latter are entirely app&#8209;specific and meant to ***replace*** use of the repos.

I have no issues with containers, but I have a number of reservations with alternate packaging systems.

---

### Post by ian-weisser on 2023-02-24
It depends upon the circumstances.

My own opinion is that I see a lot of *lazy* enthusiam for both (especially for Docker containers). It's fun to code, to use bleeding-edge dependencies, to release often. It's easier to push the update burden onto the user. But that's the path to niche acceptance. Users don't want to mark their calendars to check for updates every month. Users don't want to learn (and track) lots of different packaging systems.

We went through this with PPAs, too.

It takes some hard work to get software into Debian, and to keep it there. But it's generally worth the effort. Simply adhering to Debian standards improves the software and the documentation, widens the testing population, and gets the software into Ubuntu and in front of many more users.

---

### Post by DuckHook on 2023-02-24
&#8593; This &#8593;

Related to Ian's point, what I find to be a constant headache and source of trouble for incautious users seeking help on these forums is the penchant to "customize" everything. You just have to peruse the threads of these forums to see how much trouble people get into because they tinkered with this or monkeyed with that, often without even remembering what they did, nor how many tinkerings they made. It's little wonder that their systems get corrupted beyond the point of no return.

We all have a childlike tendency to reach for that shiny new toy. But, like one of our members (TheFu) is fond of saying, "new is the enemy of stable". Do we *really* need that latest and shiniest version of an otherwise reliable app? Or is it just a manifestation of the (irrational) fear&#8209;of&#8209;missing&#8209;out syndrome?

---

