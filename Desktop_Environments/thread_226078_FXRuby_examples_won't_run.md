---
title: "FXRuby examples won't run"
date: 2006-07-30
forum: Desktop Environments
---

### Post by teryret on 2006-07-30
Would anyone here mind walking me through getting FXRuby from where it is now to a state where I can run the example scripts that it comes with? I'm still not quite to the level of linux pwnership where I have an intuitive sense of what I need to do next.

So far, I have (AFIAK) installed ruby 1.8 (and indeed I can write and run text based scripts), gems 0.9.0 (I think its working...), fox16 (/usr/lib/ruby/gems/1.8/gems/fxruby-1.6.1/ext/fox16/fox16.so exists... or at least that's what ls tells me, it could be a nefarious plot of some sort), and fxruby1.6.1 (whose installer claims to have succeeded, but I have my doubts).

When I run the hello.rb script from the examples directory (that came with FXRuby) I get the following error: 
Code:
./hello.rb:3:in `require': no such file to load -- fox16 (LoadError)
        from ./hello.rb:3

Google lead me to [http://rubyforge.org/pipermail/fxru...uly/000928.html](http://rubyforge.org/pipermail/fxru...uly/000928.html) which seems to be the exact thing I'm facing, but for some reason the solution posted didn't work.

Thanks for the help!

While I await a responce on here I'm going to try to get an older version of gem installed so that I can use it to correctly install fxruby.  The problem I expect to face is removing the old install that the newer (bugged) version of gem put on.

Edit: gem0.8.11 seems to have done the same thing... either that or I didn't uninstall the broken-ness enough.

---

