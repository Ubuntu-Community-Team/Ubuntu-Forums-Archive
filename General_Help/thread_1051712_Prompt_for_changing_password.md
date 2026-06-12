---
title: "Prompt for changing password"
date: 2009-01-27
forum: General Help
---

### Post by elf_cleric on 2009-01-27
Hi guys,
I desperately need to do following,
Does anyone knows about how to set in user profile to ask user to change his/her password after week or two?

Or ask user to change the password each time he/she logs in?

Cheers

---

### Post by iaculallad on 2009-01-27
To change the password age for a user, use the command below on your terminal:

```
sudo chage username
```

and to verify it:

```
sudo chage -l username
```

For more information regarding chage:

```
man chage
```

---

### Post by elf_cleric on 2009-01-27
Thanks mate :)
How this basically work?
Sorry, I am a beginner.

---

### Post by geirha on 2009-01-27
In your case, you can do
```
sudo chage -M 14 -W 7 *username*
```
This will make *username*'s password expire 14 days (-M 14) after it has been set. If the user tries to log in after those 14 days have passed, it will be prompted for the password, then immediately prompted to supply a new password. The user will not be able to log in before it has changed the password.

-W 7 will give a warning to the user when he logs in if there is less than 7 days until the password expires.

Also, to learn about a command, always check if there is a man-page
```
man chage
```

---

### Post by elf_cleric on 2009-01-27
Many thanks :)
How about after expiretion?
Is user totally gone?
Can user still change hes/her pass?

Cheers.

---

### Post by geirha on 2009-01-27
Yes, the user will be able to change the password long after the password expires. You can set an expiration date on the account (rather than password) too, with the -E option. Try setting it to today's date on a test user.

```
sudo chage -E 2009-01-27 *testuser*
```

and see what happens when you log in with that test user.

---

