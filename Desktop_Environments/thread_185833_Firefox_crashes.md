---
title: "Firefox crashes"
date: 2006-06-01
forum: Desktop Environments
---

### Post by zAo on 2006-06-01
Hello all,

I'd like to edit some of my blogs, but I cannot get to the page. Firefox and Epiphancy just keep crashing. Same for YouTuBe.com

```
decoding...
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadImplementation (server does not implement operation)'.
  (Details: serial 35 error_code 17 request_code 129 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Any ideas?

Thanks.

---

### Post by zAo on 2006-06-01
For the record, I use Wordpress for my blogs.

No one having these experiences?

---

### Post by beerorkid on 2006-06-01
good possibility flash might be the culprit.  It seems to bork a lot of people.  look up "firefox flash"

not sure but it might help ya.

---

### Post by bjc on 2006-06-02
Are there any similarities between the pages that are causing the crash? Can you load a bare-bones page like [http://google.com/](http://google.com/) OK? If you can rule out Flash (by removing the plugin and loading the same URLs again), create a new Firefox profile and try with that:
```

firefox -ProfileManager

```

FWIW, [http://youtube.com/](http://youtube.com/) loads fine for me using *flashplugin-nonfree*.

---

