---
title: "Ruby on Rails warning messages"
date: 2009-05-12
forum: General Help
---

### Post by vhenry on 2009-05-12
Not sure if this is the correct place to post this question, but here goes. I'm running ruby 1.8.7 and rails 2.1.0 on ubuntu linux 9.04. When I run the rails command to create a new application and also the ruby/script server command from the terminal window, I get the following message:

/usr/lib/ruby/1.8/xmlsimple.rb:275: warning: already initialized constant KNOWN_OPTIONS
/usr/lib/ruby/1.8/xmlsimple.rb:280: warning: already initialized constant DEF_KEY_ATTRIBUTES
/usr/lib/ruby/1.8/xmlsimple.rb:281: warning: already initialized constant DEF_ROOT_NAME
/usr/lib/ruby/1.8/xmlsimple.rb:282: warning: already initialized constant DEF_CONTENT_KEY
/usr/lib/ruby/1.8/xmlsimple.rb:283: warning: already initialized constant DEF_XML_DECLARATION
/usr/lib/ruby/1.8/xmlsimple.rb:284: warning: already initialized constant DEF_ANONYMOUS_TAG
/usr/lib/ruby/1.8/xmlsimple.rb:285: warning: already initialized constant DEF_FORCE_ARRAY
/usr/lib/ruby/1.8/xmlsimple.rb:286: warning: already initialized constant DEF_INDENTATION
/usr/lib/ruby/1.8/xmlsimple.rb:287: warning: already initialized constant DEF_KEY_TO_SYMBOL
=> Booting Mongrel (use 'script/server webrick' to force WEBrick)

Any idea what this means? How can I stop it?

---

### Post by vhenry on 2009-05-15
solved by reinstalling ruby & rails.

---

