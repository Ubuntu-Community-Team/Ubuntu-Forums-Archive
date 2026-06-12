---
title: "I need urgent help!!!"
date: 2009-05-08
forum: General Help
---

### Post by Keri.K on 2009-05-08
I have a project that I have to do, where I have to write a program for the game hangman. Problem is that I'm not very good at programming and I dont know where to start. Can anybody please help me?

---

### Post by StOoZ on 2009-05-08
In what language do you need to do it?

---

### Post by slackthumbz on 2009-05-08
does this version of hangman need to be graphical or can you do it in ncurses? perl has fairly good hooks for GTK and ncurses so you might want to look at that.

As for where to start you'll probably want to create a wordlist from which the game can randomly select a word to play with.

in perl:
```

my @array;
open WORDLIST, "</path/to/wordlist.txt";
while (<WORDLIST>) { chomp($_); push @array, $_ };
close WORDLIST;
my $word = $array[int(rand(scalar(@array) + 1))];

```
etc...

If you want to make things really easy for yourself I'd suggest doing it in javascript and xhtml.. but I wouldn't really call that programming ;)

I'd also recommend looking at the source code to an existing solution. But in all seriousness this is _your_ project and if you're not good at coding then you should see this as an opportunity to improve.

---

### Post by Keri.K on 2009-05-08
It has to be in C++. The program basically has to read a random word from an external file that contains 20 words for the game to start. I would appreciate any help I can get cause I'm not at all sure on how to go about it.

---

### Post by Legace on 2009-05-08
Why are you doing a project in a language you don't know how to use?

-- or --

Why are you doing something that's hard for you, if you don't know the basics..?

---

### Post by Keri.K on 2009-05-08
I just started programming so I'm still getting used to it. I can open the external file, but getting a random word out of it is something I'm finding difficult to do.

---

### Post by wirelessmonkey on 2009-05-08
These forums aren't an appropriate place to ask people to do your homework for you.

---

### Post by Mirge on 2009-05-08
> **Keri.K said:**
> I just started programming so I'm still getting used to it. I can open the external file, but getting a random word out of it is something I'm finding difficult to do.

See if [http://www.daniweb.com/forums/thread8335.html#](http://www.daniweb.com/forums/thread8335.html#) helps you with the random issue at all. I don't think anybody here is going to do your homework for you, but I'm sure they wouldn't mind helping you actually learn it.

---

### Post by mhaight on 2009-05-08
> **wirelessmonkey said:**
> These forums aren't an appropriate place to ask people to do your homework for you.

I agree, this isn't the place for this, just talk to your instructor or a classmate.

---

### Post by Tipped OuT on 2009-05-08
> **wirelessmonkey said:**
> These forums aren't an appropriate place to ask people to do your homework for you.

He's not asking any one to do his home work for him, he's asking for help, where to start first because he has no idea.

---

### Post by Keri.K on 2009-05-08
I am not asking anyone to do my homework for me. I am just stuck and I was hoping there would be someone on here to help me out.

---

### Post by Legace on 2009-05-09
> **Keri.K said:**
> I am not asking anyone to do my homework for me. I am just stuck and I was hoping there would be someone on here to help me out.

You should ask somewhere else for help with programming. I'm sure there are forums dedicated for that purpose. Google is your friend :)

---

### Post by Alterax on 2009-05-09
Well, before you so much as open a text editor, I really can't recommend enough that you grab some paper and a pencil.

Tackling the whole problem at once is going to be overwhelming.  Break it down into steps:  Picking a word, set up a counter with the amount of tries a user gets, getting a user's letter as input, checking that against the string, and counters for success and failure.

Once you break it down into manageable chunks and have your workflow mapped out, it gets a LOT easier.  Pick a piece out of the chart and code it (functions are your friend), move on to the next bit, then finally string them together in your main section to fit your workflow.

When I program, I spend about an hour at the whiteboard to 20 minutes programming.  It seems like a lot more work (I've even gotten in trouble for it from clients who think programs are supposed to flow like magic directly from the ether to the keyboard), but it's a lot LESS work to break it down, plan it out and get a good picture of what you are trying to accomplish in each piece.

---

### Post by bapoumba on 2009-05-09
> **wirelessmonkey said:**
> These forums aren't an appropriate place to ask people to do your homework for you.

*watching*.

---

