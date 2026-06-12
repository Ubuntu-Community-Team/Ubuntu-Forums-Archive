---
title: "Amarok lyrics script error."
date: 2008-12-02
forum: General Help
---

### Post by Jerfo on 2008-12-02
Hello! This error began yesterday, the lyrics script had been working fine but suddenly it kept giving me an error message everytime I tried to get lyrics or to run it from the scripts manager, I thought it'd fix spontaneously once I had rebooted but today it's the same thing, I copy paste the error message I get with one of the scripts, none of the two it comes with work, I get the same error message:

/usr/share/apps/amarok/scripts/lyrics_astraweb/lyrics_astraweb.rb:57:in `fetchLyrics': undefined method `[]' for nil:NilClass (NoMethodError)
	from /usr/share/apps/amarok/scripts/lyrics_astraweb/lyrics_astraweb.rb:56:in `each'
	from /usr/share/apps/amarok/scripts/lyrics_astraweb/lyrics_astraweb.rb:56:in `fetchLyrics'
	from /usr/share/apps/amarok/scripts/lyrics_astraweb/lyrics_astraweb.rb:139
	from /usr/share/apps/amarok/scripts/lyrics_astraweb/lyrics_astraweb.rb:125:in `loop'
	from /usr/share/apps/amarok/scripts/lyrics_astraweb/lyrics_astraweb.rb:125

So... since I don't understand anything of this, could you tell me what's the problem here and how I could solve it? It's not like lyrics are necessary for my continued existence but it sure is nice to have that little plugin.

---

### Post by Diabolis on 2008-12-02
[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/250942](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/250942)

I use Wiki-Lyrics.

---

### Post by Jerfo on 2008-12-04
I tried using wiki lyrics, but it said something about me needing to have QtRuby, RubyGTK or something else to run it, so I remained with the ones it came with.

---

### Post by Jerfo on 2008-12-04
Oh and thanks for the link, it was quite helpful.

---

