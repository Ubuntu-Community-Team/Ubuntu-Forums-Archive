---
title: "User Interfaces"
date: 2007-04-07
forum: Desktop Environments
---

### Post by PigCorpse on 2007-04-07
Hi,

I'm currently working on a research project dealing with user interfaces. However, I really have no idea where to start. So I was hoping you can post your opinions about ANYTHING dealing with interfaces. It can be something you like, hate, want improved, want implemented, anything you want, no matter how trivial. It can be as crazy as you want, no need to stick with the standards of today, for we don't know if those standards are the best solution, which is the gist of my project.

Thanks, and post away!

---

### Post by ahaslam on 2007-04-07
Elegant simplicity is the way to go ;)

---

### Post by solar george on 2007-04-07
It would be interesting if there was a GUI that was entirely designed in alpha shades of black, you'd then pick any colour be the underlying colour, and everything would be rendered in shades of it.

---

### Post by solar george on 2007-04-07
> Elegant simplicity is the way to go 

Yes I agree on that.

---

### Post by PigCorpse on 2007-04-07
Well, I'm really trying to focus on the non-aesthetic aspects of it. I'm thinking of starting first on the invisible aspects, then after that's done, make some well designed themes for it.

I really need some ideas lol.

---

### Post by hikaricore on 2007-04-07
[http://en.wikipedia.org/wiki/Graphical_user_interface](http://en.wikipedia.org/wiki/Graphical_user_interface)
[http://en.wikipedia.org/wiki/History_of_the_graphical_user_interface](http://en.wikipedia.org/wiki/History_of_the_graphical_user_interface)
[http://toastytech.com/guis/guitimeline.html](http://toastytech.com/guis/guitimeline.html)


useless links that may help you :)

---

### Post by PigCorpse on 2007-04-07
Thanks, I'm currently in the processes of reading all the Wikipedia articles dealing with UIs that I can find, plus some online articles as well, like KDE and GNOME UI guidelines.

The thing is though, that my project has to be innovative, so what would be really nice is if you can just express your opinions on stuff.

For example, I hate it when some program thinks it knows what's best for me and makes everything all automated or with some sort of tutorial.

---

### Post by solar george on 2007-04-07
Everything should be environment independent (apart from a few VERY standard services). What I mean is I should be able to take Xpanel and use it with Ydesktop without it launching services for Xdesktop.

Everything should be modular (similar to last point) each program should just do its own stuff not try and do everything. Having several programs pulled together by a GUI that sets up the options is fine though as long as they don't depend on it being there.

All config should be stored in human readable format.

Here's my thoughts, hope that they're along the lines that you want.

---

### Post by ardchoille42 on 2007-04-07
My biggest complaint in gui apps is the fact that you click File -> Quit and some apps ask you "Are you sure?". Now I can see that some folks may click on Quit by mistake and need to be able to back out of the quit, but I feel that all gui apps should have an option to "Turn off stupid questions" or something like that. I mean, if I clicked the quit button I obviously want to quit so I don't need the app asking me if I'm sure. Then the user can choose, in the apps' config, whether or not they want to be bothered by stupid questions.

---

### Post by PigCorpse on 2007-04-08
> **solar george said:**
> Everything should be environment independent (apart from a few VERY standard services). What I mean is I should be able to take Xpanel and use it with Ydesktop without it launching services for Xdesktop.

Everything should be modular (similar to last point) each program should just do its own stuff not try and do everything. Having several programs pulled together by a GUI that sets up the options is fine though as long as they don't depend on it being there.

All config should be stored in human readable format.

Here's my thoughts, hope that they're along the lines that you want.

Hmm, I like the advice and I also feel the same way. Thing is, I'm not really focusing on how the programs should be designed and implemented, but more like just the human-computer interaction. As for the last thing about config files... I'm not nearly an experienced Linux user, but I think one of the main reasons that people like using the CLI to manipulate config files is that GUI apps are slow and cater to beginner users (e.g. GUI configs don't contain all the possible options, etc). I just had an idea... Maybe you can have a GUI config window, and inside the window, you have a sort of menu/list of all the possible options (assuming the developers document every option properly). Then there is a box where all the actual options go. Like, say this is for a web browser. The user selects "Cache" from the menu. The box where the actual options go now shows all the possible thing dealing with cache, like cache on/off, size, etc. Now, next to all that is an actual text box that shows the appropriate config file, exactly as if you were editing it with nano or whatever. Whenever you mouseover an option, the corresponding line in the config file is highlighted, and you can change it using the options boxes or type it into the text box.

Now that I've typed all of that, the idea seems so unnecessary and pointless :( .

> **ardchoille42 said:**
> My biggest complaint in gui apps is the fact that you click File -> Quit and some apps ask you "Are you sure?". Now I can see that some folks may click on Quit by mistake and need to be able to back out of the quit, but I feel that all gui apps should have an option to "Turn off stupid questions" or something like that. I mean, if I clicked the quit button I obviously want to quit so I don't need the app asking me if I'm sure. Then the user can choose, in the apps' config, whether or not they want to be bothered by stupid questions.

Yeah, that's one of my pet peeves as well. That's likely going into my paper, in the section that says "Don't ask stupid questions."

For this paper, I'm probably going to target the people with a moderate amount of experience. Beginners tend to like everything in the form of a tutorial, like when you're opening up Nero or some other beginner-friendly CD burning app and you see "Burn a CD", "Rip a CD", "Copy a CD", etc. Then on the other end of the spectrum, you see people who can use a computer without a desktop environment at all. All they need is emacs. Those people are likely going to use CLI above all else (since most GUI apps are just pretty versions of CLI apps).

I consider myself in the category of a moderately experienced user. I use GUI apps like kcontrol, but if it's for advanced stuff like xorg.conf, I would use nano to edit it.

---

### Post by PigCorpse on 2007-04-10
Bump

---

### Post by solar george on 2007-04-10
I don't like it when themes/window managers try to 'reinvent the wheel' with the close minimise and maximise buttons. i.e. When a theme has replacement icons for them and the only way you know them apart is by the position.

I think a better way of saying that is I dislike it when GUIs try to look different from OSX/Windows just for the sake of it, the fact that some things are consistent shows that nobody has thought up a significantly better/more usable design yet.


GUIs that interact with the user in a different way I don't mind though, its just when programs that interact with the user in a similar way to others try and appear to be different.

---

