---
title: "Evolution help"
date: 2006-06-11
forum: Desktop Environments
---

### Post by emre on 2006-06-11
Hello everyone,
This is my first post, and i am a relatively new user to ubuntu. But I can easily recognize that this is such a great community here. So I am really happy to be some part of it.

Well as for my problem, I was trying to use evolution as my mail program. But F1 help doesn't exist and I am having difficulties with it. I made a search before posting, I hope I am not making a useless thread.

First I am looking for a way to comfortably manage the mail rules. I have 3 accounts in it and I created 3 different folders for each under inbox. I set some rules for the mails but I am not sure they are working fine. Is there any way to manage the rules from one place?

Secondly, the images in the messages are turned of by default as usual. I couldn't figure a way to enable them.

These are some of the reasons that i am uncomfortable while using evolution. Can you help me or at least can anyone direct me to the original help files?

Or should I give up and switch to Thunderbird before it is too late?

Thanks in advance.

---

### Post by johnc4510 on 2006-06-11
I use Thunderbird, but have used Evolution in the past. You can access the help files by doing this:
System>Help>System Documentation
In the search box, type in Evolution Mail

---

### Post by emre on 2006-06-11
Thanks for the quick answer John.
Well I checked and saw that System>Help>System Documentation was missing in my ubuntu dapper installation - in fact it is a default installation. Strange. 

So there was online help but it only covers quick desktop help.

---

### Post by johnc4510 on 2006-06-11
Check in Synaptic Package Manager to see if Yelp is installed, if it is not install it. If you need help with that, post back here.

---

### Post by emre on 2006-06-11
Yay that did the trick thanks alot. 
cheers

---

### Post by dpm on 2006-06-11
[quote=emre]But F1 help doesn't exist and I am having difficulties with it.[/quote]

This is really weird. But I do not quite understand what you mean by "F1 help doesn't exist". Does pressing F1 not work at all? Does it happen in other GNOME applications? What about going to the Help>Contents menu, does that work?

[quote=emre] First I am looking for a way to comfortably manage the mail rules. I have 3 accounts in it and I created 3 different folders for each under inbox. I set some rules for the mails but I am not sure they are working fine. Is there any way to manage the rules from one place?[/quote]

AFAIK, the only place to manage filters is from where you've already defined them, that is, Edit>Message Filters. So that's your central place.

[quote=emre]Secondly, the images in the messages are turned of by default as usual. I couldn't figure a way to enable them.[/quote]

Go to Edit>Preferences>Mail Preferences>HTML Mail and choose either "Load Images in Mail from Contacts" or "Always Load Images From the Internet".

I hope this helps.

Cheers.

---

### Post by dpm on 2006-06-11
[quote=emre]Yay that did the trick thanks alot. 
cheers[/quote]

Ignore the first part of my last post, I hadn't seen your message before I had started typing.

---

### Post by emre on 2006-06-11
Thanks for the details.

Yes after installing yelp, the help inside evo is working fine too. 

Those rules are pretty annoying :P, i wish it would set my accounts to their own local folders - as it can be done automaticaly in thunderbird.

And for the last one, you mean there is no way to look at the message and then decide to load the images? bad:(

---

### Post by dpm on 2006-06-11
[quote=emre]Those rules are pretty annoying :P, i wish it would set my accounts to their own local folders - as it can be done automaticaly in thunderbird.[/quote] 

I find these rules (IIRC they are not called rules but filters in Evolution) quite powerful and easy to set up. The thing is, I do not quite understand what you are trying to do. So please be more detailed so I or someone else can help you.

[quote=emre] And for the last one, you mean there is no way to look at the message and then decide to load the images? bad:([/quote]

I'm not sure if that's what you mean, but if you've chosen not to load images per default, you can still see the pictures by selecting the message and going to View>Load Images. Or alternatively use the shortcut <CTRL+I>. BTW, Outlook does exactly the same, only that there you have to right-click on the image and tell it to download it.

So basically you've got 3 options: "Never Load Images from the Internet", "Load Images in Mail from Contacts" or "Always Load Images From the Internet". If images are not loaded, you can always download them afterwards with <CTRL+I>. It cannot get more customizable than this.

Cheers.

---

### Post by emre on 2006-06-12
Well thanks for your kind efforts to get me going:P.

For the image part I got it thanks to your detailed explanation.

For the rules, all I am trying to do is, set my each account to their own folders, seperate inbox, sent box for each different account. In thunderbird you choose this function while or after creating an account. Some people talk about vFolders to be evo's great strength, but I think they are a little too much for me now.

Emre

---

### Post by dpm on 2006-06-12
[quote=emre]For the rules, all I am trying to do is, set my each account to their own folders, seperate inbox, sent box for each different account. In thunderbird you choose this function while or after creating an account. [/quote] 
Evolution and Thunderbird are two completely different programs. The way they handle folders/accounts is also completely different. I must admit it took me some time to get used to the way Evo handles folders/accounts/filters. But now that I know how it works, I find it more powerful and easy to setup than Thunderbird. I've been a user of Outlook Express, Outlook and Thunderbird, and I find Evolution to be the best of them. That's simply my personal oppinion, other users may find e.g. Thunderbird better. It's all about finding the application that suits your needs.

a) In case you want to keep the setup of 3 separate folders, you simply have to define a filter for each one of the folders. For example, you can set up a filter for incoming mail, which will be active when the recipient is <your-account-1@blahblah.com> and then will move the message to the appropriate folder. The other two filters will be exactly the same, only that the recipient and folder criteria will have to be adjusted for the appropriate account/folder pair. All mail will go through the Inbox and will then be filtered and redirected to the appropriate folder for each account.

b) What you coud also do is **not** to create the 3 physical folders under the Inbox, but create 3 virtual folders with the same filter criteria of option a) instead. To create a vFolder, simply right-click on "Search Folders" and select "New Folder", which will take you to a dialog which will allow you to specify the filter criteria. In this case, all mail will physically reside at the Inbox, but you can still have sepparate views of each account through the search folders. Think of a search folder as a view or symlink, if you like.

[quote=emre]Some people talk about vFolders to be evo's great strength, but I think they are a little too much for me now.[/quote] 
Once you understand the concept, they are very easy to set up, see the previous paragraph.

Cheers.

---

### Post by emre on 2006-06-13
[QUOTE=desp]Think of a search folder as a view or symlink, if you like.
[/QUOTE]

Hmmm, sounds delicious. :P They seem like gmail's system. 

Actually I had created those physical folders. And created those "recipient" rules before posting here. Then I figured they don't work well and saw that there is another rule filter "source account". I said well this is my solution but it didn't do it either. 
 
I think my gmail pop messed up all. Because not only the incoming ones, all the  mail stored in gmail is being downloaded. I think it's about the way gmail handles the sorting. For this reason, my inbox is full of gmail messages which refuse to go gmail folder. That "source account" filter didn't work either.

For thunderbird comparison, I think evolution is much more advanced, no need to be geinus to see that. It's jut that account seperation that I miss.:P

BTW your posts are really clear and well organised. Thank you very much.

---

