---
title: "Ubuntu Desktop Life Cycles"
date: 2006-09-04
forum: Desktop Environments
---

### Post by wildcard58th on 2006-09-04
I'd like to understand the exact timeline for (the desktop) life cycles within Ubuntu.

At present we have Dapper which is to be supported for 3 years. In the pipeline we have Edgy.

Will we have 5 more versions (ala Edgy) before another 'LTS' (ala Dapper) release?

If this is the case will updated applications (e.g. Evolution) and libraries (e.g. Python) be made available for Dapper, say in 12 months time.

What I'm getting at is; is it the case that say 8 months before the support for Dapper LTS runs out the applications will be (so) dated that people will be making ad-hoc binaries or simply using a 'Edgy' type version of Ubuntu?

---

### Post by skymt on 2006-09-04
Ubuntu uses a four-version cycle. The first was Warty, followed by Hoary, Breezy, and now Dapper (LTS). Edgy is the start of a new cycle, so Edgy+3 will be LTS like Dapper.

Dapper won't be getting new versions of applications. That would be pointless. If you want the new versions, you should upgrade to the latest distribution version. The reason Dapper is LTS is that they feel the current versions are stable enough together to support for three years. If they were to upgrade packages beyond security and bug fixes, it would reduce the stability and create a "moving target" for quality control.

---

### Post by wildcard58th on 2006-09-04
Thanks for the answer. Thats much clearer.

Just playing devils advocate for a min, while keeping your point about QA at the front of ones mind.

Is there not an argument to be made that by the time of "Edgy+3" that key applications such as Evolution, Openoffice and Firefox will be outdated in terms of features/functionality?

For example, by Edgy+3 Mozilla will have (one assumes long) depreciated Firefox 1.5.x in favor of Firefox 2.x , yet Dapper will not officially support Firefox 2.x..

Does this not create a situation where software vendors, Mozilla in this case, are marketing and advocating a product version (Firefox 2.x), while Ubuntu stands by a depreciated version?

Factor in the likely client base of Dapper LTS (enterprises, schools, NGO's SME's) and their use cases (Software as a services being an ever increasing use case) and a 2 year+ old web browser (Firefox 1.5.x) could be unsuitable.

Perhaps a browser is a unique case of software but can you not make the argument that 'certain' key applications could do with being refreshed, arguably in line with their vendors release cycle, granted, slightly (i.e. not 2+ years) delayed for QA purposes.

Again though...devils advocate :-| 

Cheers

---

### Post by skymt on 2006-09-04
Take my school as an example. The computers in the library have Netscape 7 on them. This was standardized when NS7 was fairly new (4 years ago). It still works fine on most sites. Three years isn't really that bad.

If Ubuntu were to upgrade Dapper to, say, Firefox 3, this would be a big enough change that somewhere, in some IT department, something would break. Some of the larger applications will probably be backported for the first couple years (-ish, I don't know specifics), but the main distribution will stick to essential fixes.

---

