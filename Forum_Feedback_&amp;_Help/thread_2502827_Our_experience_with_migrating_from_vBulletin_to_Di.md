---
title: "Our experience with migrating from vBulletin to Discourse"
date: 2024-12-01
forum: Forum Feedback &amp; Help
---

### Post by thecrius2 on 2024-12-01
Hi, I registered because I read from Reddit that you are thinking of moving from vBulletin to Discourse.

I am the admin for a community that exists since 2002 (not admin since then, just the past couple years) and at its peak had thousands of active users, which means we had a huge database of topics and replies (20M replies and 500k topics roughly).
I am doing this to give you an idea of the issues you might be facing. This whole topic can be ignored in its first part (migration) if you plan of paying Discourse for the hosting as they will probably take care of it themselves.

The reason we looked at a migration is that our vbulletin was stuck at the 3.x version as nobody had administered the forum for years. Updating to vbulletin 4 and then 5 would have been disruptive as change entirely platform and as we are self-funded, we decided it was a good moment to look at free and open source options as we were willing to invest time to make it work rather than keep giving license money to vbulletin as it felt kind of stagnant in its features.

I started by testing the migration scripts that are available and noticed first thing that the scripts takes ages to go through the records. However, the major issue is that at some point it just invokes function(s) that are just not present in the script. When asking the discourse forum itself, someone mentioned the script not being finished.
Luckily, the community was formed by a good amount of tech-savvy people. Lots of us joined it for the love of gaming in its infancy (early 2000) and then made a career of the passion for all things related to computers and programming.
We managed to put together a small team, me and other 2&#8211;3 people that simply wrote a migration script in c# ad-hoc for our forum database by reverse engineering how discourse worked and how the database was structured. It took us around 3 months of working after working hours and doing some late nights, but we had enough laughs in the process and the love for our community carried us forward.

So, first warning is: [B]Be ready to get your hands dirty and have to potentially write a migration by yourself.

[/B]After the migration (we managed to have it complete, avatar and other non-db related things included in about 4 hours) we thought things would be fine. And it did, for the most part. We had the occasional hiccup but we sorted it out. The two main issues I want to raise and need to be considered are:

- If you are on the "test-passed" tag (default for self-hosted) be ready for some breaking changes being deployed. You are effectively the QA for the software. If you don't want to risk it, I suggest using instead a precise stable tag.
- Be aware that if you are not on the `test-passed` tag, however, you will not get support unless using a fairly recent version. In which case the suggestion will be "update to the latest version"
- Discourse struggles a lot with big databases. This is due to both the database design and the code design. After the migration we got help from another user that is a professional ruby-on-rails developer and the amount of cursing I have heard that man says when describing the codebase made me worried about my chance at paradise.
- Just recently, I have had to dig around to find that a script that measure the *time each of the users read the forum* was slowing our hosting to a crawl. For reference, our host is a 8 vcpu, 32GB RAM, 500 nvme SSD.
- Last but not least, all the most crippling problems I have found, have mentioned in the discourse forum, sometime years old. Those topics are either dead, without response, or the user itself post a workaround or there is a reference for a fix in a patch. Except, if that patch was deployed, down the line someone must have reintroduced the issue otherwise I wouldn't have to go and search for solutions

Overall, my opinion is that discourse is not a forum meant for big established communities but for modern ephemeral ones. Like gaming companies release their game. See Last Epoch (game), Fatshark (game company) or World of Warcraft forum, which consist of spike in activities that then get archived or forums that "die" after a big and never hit big numbers that would incur in issues.

In conclusion, be careful with this migration and if you think of doing this because of getting more palatable to new audience, I assure you that a change of platform is not going to do that. You can get better results by integrating social networks in your community, like posting "hot topics of the week on twitter/facebook" for example, rather than migrating to a new platform.

If you want more details or have specific questions, feel free to ask here or in PM (if there is sensitive data) and I'll do my best to answer if I can.

Cheers

---

### Post by Frogs Hair on 2024-12-01
Thank you for your input. If you read the banner when you logged you'll see that the transition is in full swing. Many Linux forums are already using Discourse such as Zorin OS, Endeavour OS, and many more. The forum is moving to the well established Ubuntu Community Hub where the Ubuntu developers have done their work for some time now. A team has been at work setting-up the support categories and getting the staff ready to go.

---

