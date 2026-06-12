---
title: "adesklets mailer + gmail"
date: 2008-01-21
forum: Desktop Environments
---

### Post by danifodor on 2008-01-21
Hi!

What is the problem with the following adesklets mailer config file?

```

id0 = {'background_color': '1E1E1E',
 'background_gradient_cutpoint': 40,
 'background_opacity': 100,
 'caption': '',
 'caption_color': 'FFFFFF',
 'caption_font': 'Vera',
 'caption_font_size': 10,
 'click_anytime': False,
 'delay': 300,
 'host': 'imap.gmail.com:993',
 'icon_height': 48,
 'icon_width': 48,
 'icons': ['error.png', 'noemail.png', 'email.png'],
 'mailspool': '/dev/null',
 'message_color': None,
 'message_font': None,
 'message_font_size': None,
 'messages': ['connection error',
              'no new message',
              '1 new message',
              'new messages'],
 'messages_prepend': True,
 'method': 'imap4',
 'program_on_click': None,
 'program_on_new': 'beep.sh',
 'ssl': True,
 'text_padding': 5,
 'user_name': 'dnlfdr',
 'user_password': 'xxxxx',
 'window_never_shrink': False}

```
I get always connection error message...

Any idea?

Thanks

Daniel

---

### Post by bleunuit on 2008-02-17
The following are my configuration files. 
It is possible to receive it normally. 
```
id0 = {'background_color': '1E1E1E',
 'background_gradient_cutpoint': 40,
 'background_opacity': 0,
 'caption': 'GMail',
 'caption_color': 'FFFFFF',
 'caption_font': 'Vera',
 'caption_font_size': 10,
 'click_anytime': False,
 'delay': 300,
 'host': 'imap.gmail.com',
 'icon_height': 48,
 'icon_width': 48,
 'icons': ['error.png', 'noemail.png', 'email.png'],
 'message_color': None,
 'message_font': None,
 'message_font_size': None,
 'messages': ['connection error',
              'no new message',
              '1 new message',
              'new messages'],
 'messages_prepend': True,
 'method': 'imap4',
 'program_on_click': 'firefox https://mail.google.com/mail/',
 'ssl': True,
 'text_padding': 5,
 'user_name': 'username@gmail.com',
 'user_password': '*****',
 'window_never_shrink': False}

```

---

