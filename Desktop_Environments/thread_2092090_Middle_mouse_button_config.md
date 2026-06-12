---
title: "Middle mouse button config"
date: 2012-12-06
forum: Desktop Environments
---

### Post by mikesmithv on 2012-12-06
I have been having trouble with text appearing in documents that look like something I might have typed but otherwise randomly placed.  After all this time I finally figured it out.  Pressing the middle mouse button (scroll wheel) performs a "paste" in Ubuntu, so whatever I copied previously gets randomly "pasted" into my documents when using the scroll wheel too hard.  Not good.

My question is how can I disable the scroll wheel from acting like a button?  I found [this link]("https://wiki.ubuntu.com/X/Config/Input") which seems to indicate others are having this problem:

[https://wiki.ubuntu.com/X/Config/Input]("https://wiki.ubuntu.com/X/Config/Input")

> Scrollwheel mice support a middle-button click event when pressing the scrollwheel. This is a great feature, but you may find it irritating. Fortunately it can be disabled.

The solution they present there disables the middle button temporarily but the original configuration returns if I restart or the mouse goes to sleep and is re-awakened.  Does anyone know of a way to set this configuration permanently?

These are the steps that did not work.  First I get the mouse ID:
```
xinput list | grep 'id='
```

For me the mouse ID was 13.  So next I get the current mapping:
```
xinput get-button-map 13
```

It returned 1 2 3 4 5 6 7.  Then I write back my altered map replacing the 2 with a zero:
```
xinput set-button-map 13 1 0 2 3 4 5 6 7
```

Like I said, this fix works temporarily but I think I need to edit some config file further upstream where the defaults are set since it keep reverting.

I suspect many others are having this problem but have not figured out what's happening yet since it happens so seldom.  I seems to me that it's more of a bug than a feature.  The default should be to not let unsuspecting users paste text randomly.  It's fine to have this as a feature but it's definitely something that should be enabled by the power user IMHO.

---

### Post by Krytarik on 2012-12-06
You should be able to achieve that using "xmodmap", works for me at least. For that, create a file called ".Xmodmap" (hidden) at the top level of your home directory with this content:

~/.Xmodmap:
```
pointer = 1 0 3 4 5 6 7
```The next time you log in, you may be asked if you want to use that keymap file.* If so, just choose "Add" and confirm with "OK". It should work then.

* depends on what Ubuntu version you are using, and if you already had such a file before, and have already confirmed/disabled that query

Regards.

---

### Post by mikesmithv on 2012-12-06
That fixed it.  Thanks.  I'm using Ubuntu 12.10 and there was no message, it just came up configured when I logged in.  Thanks again, that was really causing me problems.

---

