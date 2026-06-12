---
title: "Putting ogmrip in the background from terminal"
date: 2012-02-12
forum: Desktop Environments
---

### Post by unckybob on 2012-02-12
Hi,

I already have an instance of ogmrip running. I would like to start a new instance of ogmrip and execute a script after the new instance finishes. I have tried this:

# ogmrip ; bash script_file &
mencoder: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
mplayer: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
mencoder: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
mencoder: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
mencoder: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
mencoder: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
mencoder: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking

This works, but it doesn't seem to go to the background. I don't get a prompt after running the command and I would like to get rid (control-D) of the terminal.

Can someone tell me how to make this work right?

---

### Post by savanna on 2012-02-12
The semicolon is your problem - it means "do ogmrip, then when you're finished do bash scriptfile and go into the background".

Try:

(ogmrip ; bash script_file) &

ie use a subshell

Also, if you don't want the output of ogmrip all over the screen:

(ogmrip &> /dev/null ; bash script_file) &

---

### Post by unckybob on 2012-02-12
Thanks, that worked.

---

