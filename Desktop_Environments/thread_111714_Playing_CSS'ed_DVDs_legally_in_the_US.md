---
title: "Playing CSS'ed DVDs legally in the US"
date: 2006-01-02
forum: Desktop Environments
---

### Post by OneSeventeen on 2006-01-02
I live in the United States and I want to play encrypted DVDs legally.

What do I do?  (I understand this may mean purchasing software, but I'm okay with that, and want to know *what* to purchase and *where* to purchase it from.  I'd hate to buy a program that doesn't work well with Ubuntu.)

---

### Post by Ampersand on 2006-01-02
You need to install regionset (available from apt), then run it from a terminal in order to set your drive to a certain region. Run
```
regionset -h
```
or
```
man regionset
```
to see how to use it.

---

### Post by ltmon on 2006-01-02
Unfortunately there's very little commercial DVD playing software available for Linux... it just isn't made because of the smaller market.

The options you have are:

- Trying to get a DVD playing program working with Wine.  Have a look in the applications database at [http://winehq.org](http://winehq.org) for DVD players.  The comments there should give the best indication of whether or not it will work on Ubuntu.
- Morally justifying your use of the decss codec with the reasoning that you have already bought a DVD drive and related (windows only) software, which includes a licenced copy of the codec, and have therefore payed your licence fees to the DVD consortium and owe them not a penny more :).

L.

---

### Post by OneSeventeen on 2006-01-02
Thanks, looks like I'm SOL.

Any tips on who I can talk to about getting a CSS license?  As a software manufacturer, anyway.  I would love to find a way to write a linux DVD player and let my company hold the CSS license.  It would probably have to be closed-source and proprietary, but the license would read something like:

"You agree to use this only for the legal playback of CSS encrypted DVDs, and will not be used to circumvent CSS encryption.  By using this software you agree to take all responsibility, financial and otherwise, for breaching this contract to all respective parties.  This product comes with no garuntee or warranty, etc. etc.  You may not reverse engineer this, or do anything that may make it possible to use this software to circumvent CSS encryption in any way, shape or form.  (for that use libdvdcss if you are in a country that allows such circumvention)"

Then all I'd have to do is raise the $10,000USD or whatever it costs nowadays for a CSS license, and once that amount has been donated, just give the DVD decoder away for free.  (Maybe the ubuntu foundation could run a fundraiser and use some core developers to write this, and make it a huge perk that makes Ubuntu ideal for home-users in the US?)

I'd gladly drop a few bucks in the collection bin for this.  Any ideas how to get this started?

---

### Post by ltmon on 2006-01-02
Well the people to talk to are: [http://www.dvdforum.org/](http://www.dvdforum.org/)

But they are _big_ companies, and as such small guys like yourself will have the usual trouble.

I think the CSS licence is royalty based, i.e. you have to pay them $x for every DVD player you ship.  So actually "purchasing" a licence is not straightforward.

Also, Ubuntu won't accept any closed source or otherwise non-free program into the default repository.  That is why even MP3 players are not included in Ubuntu by default.

Good luck in any case.

L.

---

### Post by Spyderizer on 2006-01-02
Regionless DVD players are available in lots of places outside the US. No one's losing any money by giving linux users the ability to play DVDs, and considering that software such as libdvdcss can only be used to play legitimate legally purchased DVDs in the first place, it's a pretty damn stupid law.

---

### Post by OneSeventeen on 2006-01-02
Well, according to the technical FAQs from the DVD Forum, DVD video quality is good, and DVDs are the same size as CDs.

Wow, those guys are really on the ball with their image to the general public.

(sorry, it's frustrating when their FAQ isn't really helpful, and they don't have a contact number anywhere.)

I have a current business plan that will hopefully have at least $2million USD in my business account in the next 4 years, so I'm serious about trying to get a free DVD decoder, but then again, I feel the US court system should find a way to make DVD's playable for free on any operating system.

For now, I think I'll just avoid purchasing encrypted DVDs.  Are there markings anywhere to say which DVDs are encrypted and which are not?  I sincerely hope so, otherwise I'd consider it false advertising to show DVD video implying it could be played in a DVD video playing device without mentioning the need for an extra after-market DVD decoder.

Bah, why can't everyone be as smart as GNU-related developers?

---

### Post by doclivingston on 2006-01-02
[QUOTE=OneSeventeen]For now, I think I'll just avoid purchasing encrypted DVDs.  Are there markings anywhere to say which DVDs are encrypted and which are not?  I sincerely hope so, otherwise I'd consider it false advertising to show DVD video implying it could be played in a DVD video playing device without mentioning the need for an extra after-market DVD decoder.[/QUOTE]

Basically: if it's mass-produced, it will be encrypted. There are the occasional exceptions, but as a rule anything you buy will be encrypted.

---

### Post by mcduck on 2006-01-03
[QUOTE=Spyderizer]Regionless DVD players are available in lots of places outside the US. No one's losing any money by giving linux users the ability to play DVDs, and considering that software such as libdvdcss can only be used to play legitimate legally purchased DVDs in the first place, it's a pretty damn stupid law.[/QUOTE]
CSS and region codes are two different things. Even 'region-free' region code 0 discs use CSS.

---

### Post by nocturn on 2006-01-03
I think PowerDVD has a Linux version, not free though.

---

