---
title: "Testing mailto: in web form"
date: 2009-04-01
forum: General Help
---

### Post by Volt9000 on 2009-04-01
I'd like to be able to test out HTML post forms with mailto: in them on my computer, i.e. something like....

```

<form action="mailto:my-email@address.com" method="post">

<input type="text" name="name" value="" size="20">

<input type="submit" value="Send">
<input type="reset" value="Reset">

</form>

```

I just want to be able to test this out without having to upload it to a webserver. I assume I'll need sendmail or something similar installed... can someone point me in the right direction?

[Edit]
Although it would be nice, this doesn't even HAVE to work with proper e-mail addresses... if I could get this to somehow send local mail, that would work too, so long as I can test the form.

---

### Post by kanikilu on 2009-04-03
I don't think that will work. You can't put a mailto as a form action as far as I know. You'll need a script to process the form and mail the results.

Other languages will work, but I'm most familiar with PHP (which isn't saying too much). Check out the [mail() function](http://us.php.net/manual/en/function.mail.php).

If you don't want to upload to a server, pretty much your only option is to run a server on your local host. The easiest way to setup an AMP stack is ```
sudo tasksel
``` From there just select "LAMP Server". You can also install a mail server from the same place if you want...

---

### Post by Volt9000 on 2009-04-06
Great, thanks!

---

