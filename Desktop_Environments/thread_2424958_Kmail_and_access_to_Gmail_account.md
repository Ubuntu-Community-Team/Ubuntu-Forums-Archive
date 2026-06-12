---
title: "Kmail and access to Gmail account"
date: 2019-08-18
forum: Desktop Environments
---

### Post by christian02 on 2019-08-18
Hi.

Today I discovered that KMail cannot access my Gmail account anymore. I've read that creating an app password in my Google account and changing authentication in connection settings to "Plain" instead of "Gmail" would solve this issue, but in KMail these settings are greyed out as soon as imap.google.com is typed in IMAP server name box.
[https://imgur.com/jpSpImE](https://imgur.com/jpSpImE)
Please, do you have any suggestion?

Regards.
Christian

---

### Post by speartip on 2019-08-19
First thing I would do would be to Delete the Gmail account from Kmail, then try setting it up again & see if it throws out any errors.

---

### Post by christian02 on 2019-08-19
> **speartip said:**
> First thing I would do would be to Delete the Gmail account from Kmail, then try setting it up again & see if it throws out any errors.
Already tried in the meantime, it didn't work. Error is the same, akonadi app is considered not secure by Google.

---

### Post by speartip on 2019-08-19
Have you checked your Online Accounts status. I have been known to get logged out of that for some reason.

edit... Forget that it only affects Google Drive & Youtube.

---

### Post by #&amp;thj^% on 2019-08-20
Gmail has become as fun as pulling Teeth, According to a KDE Deveolper:  This should no longer be needed - KMail supports the native (OAuth) gmail authentication with both IMAP and SMTP.
But, have you tried to-->> This is used for applications which:
[list]
    [*]- Don't look secure by Googles standards.
    [*]- Google accounts with 2-Step-Verification. [/list]

What You have to do is:
1. Go to: [https://myaccount.google.c](https://myaccount.google.c) om/apppasswords
2. Chose "Other" and name it somehow e.g. "KMail"
3. Click Generate
4. Copy generated password to your KMail as user password (without spaces) and sign in.
Or just go to [https://support.google.com/accounts/answer/185833?hl=en&ctx=ch_DisplayUnlockCaptcha](https://support.google.com/accounts/answer/185833?hl=en&ctx=ch_DisplayUnlockCaptcha) 
And follow instructions given.
[list]

    [*]Turn on 2FA for your Google account if it's not on yet.

    [*]Go to accounts.google.com -> Security -> Signing in to Google -> App Passwords.

    [*]Generate a new password, choose "Other" as the name and enter something like KMail.[/list]

    In KMail, after you get this error, close all extra windows and go to Settings -> Configure KMail -> Accounts -> Receiving -> [Click on whichever one you want to set up] -> Modify... -> Advanced -> Authentication and choose PLAIN

    If After  you get a pop-up saying that Gmail refused to authenticate with the given username/password. Then go to authenticate again using a button in that dialog box. If you don't get this, find some other way to get to that point.

    This time, after entering your e-mail address and verifying 2FA, DON'T use your actual password. Instead, use the App Password generated in step 3. Just enter it into the password field and press Enter.

    KMail "should" now work with your Gmail account.

---

