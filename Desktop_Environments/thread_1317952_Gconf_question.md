---
title: "Gconf question"
date: 2009-11-07
forum: Desktop Environments
---

### Post by diafanos on 2009-11-07
Hello!

Does anyone know what is the purpose of the *<gettext_domain>* element of a gconf schema?

Till now, noone could give me an answer (not event #gnome irc) :(

And one more question: in *<locale>* element there is the attribute *name* which in most of the cases has the value "*C*". Why is this happening and why not an "*EN*" value?

Thanks in advance...


FYI
here is a sample schema, I am talking about:

```

<gconfschemafile>
  <schemalist>
    <schema>
      <key>/schemas/apps/evince/override_restrictions</key>
      <applyto>/apps/evince/override_restrictions</applyto>
      <owner>evince</owner>
      <type>bool</type>
      <default>true</default>
      <gettext_domain>evince</gettext_domain>
      <locale name="C">
        <short>Override document restrictions</short>
        <long>Override document restrictions, like restriction to copy or to print.</long>
      </locale>
    </schema>

  </schemalist>
</gconfschemafile>

```

---

### Post by diafanos on 2009-11-10
* b u m p *

---

### Post by diafanos on 2009-12-08
my second and final :( *bumping*

---

