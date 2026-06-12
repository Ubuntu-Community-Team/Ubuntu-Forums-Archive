---
title: "Creating a launcher for Ruby programs"
date: 2006-09-03
forum: Desktop Environments
---

### Post by Hunkadoodledoo on 2006-09-03
So, I was hoping to be able to create a launcher for [RubyRipper]("http://www.hydrogenaudio.org/forums/index.php?showtopic=38418&st=0") which is a secure CD ripper for Linux, but I am running into a wall and Google is not my friend, and I couldn't find the answer anywhere in the forums either.  The thing is that the program is written in Ruby and it has a .rb extension.  When I double click the file from Nautilus, it asks me if I want to display the contents or run it.  I choose then to run it.  But, when I made a launcher for it and double-clicked it, nothing happens.  It does not run.  I don't know what I need to do for Linux to recognize .rb files as executable programs.  Help!

---

### Post by Hunkadoodledoo on 2006-09-15
Anyone have any ideas about this one?

---

### Post by Hunkadoodledoo on 2006-09-24
I hate to keep bumping this...Anyone?

---

### Post by nereid on 2006-09-24
Maybe you should install Ruby? For example

```

ruby $YOUR_FILE.rb

```

I'm sure the file has the shebang line on top, so that your system will call Ruby automatically.

---

### Post by Hunkadoodledoo on 2006-09-24
If I didn't have Ruby installed, I wouldn't be able to run it as already stated in the first post.  As for the line of code, I am not sure what to do with that.  When I double-click the file in Nautilus, it asks if I want to display the contents, run it in the terminal or just run it.  I choose to run it, and it runs fine.  If I try to run it calling Ruby from the command line I get this error:

```
/home/josh/rubyripper-0.2/rubyripper_gtk2.rb:8:in `require': no such file to load -- ./rr_lib.rb (LoadError)
        from /home/josh/rubyripper-0.2/rubyripper_gtk2.rb:8

```

Maybe that helps things.  Suggestions?

---

### Post by nereid on 2006-09-25
Sorry, that I've overread this.

You have installed RubyRipper in your own home directory and it doesn't find the file rr_lib.rb, which should be in the same directory.

---

