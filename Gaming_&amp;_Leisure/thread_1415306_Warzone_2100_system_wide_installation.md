---
title: "Warzone 2100 system wide installation"
date: 2010-02-24
forum: Gaming &amp; Leisure
---

### Post by Onehitkill on 2010-02-24
Warzone 2100 in ubuntu's repositories is very outdated, so i downloaded from the site using the automated SVN compile install script. now the warzone folder is sitting on my /home/"insert user name"/warzone directory. I already have the older version installed from the repository/software center. However two thing's concern me :

1) if i were to uninstall the older version, will it affect my current installed version?

2) [http://](http://)[forums.wz2100.net/viewtopic.php?t=3397]("http://ubuntuforums.org/forums.wz2100.net/viewtopic.php?t=3397")
I followed the instuctions and used the script here but i dont know how to run a system wide install. ( Still an absolute terminal beginner for now, but its becoming clear i need to learn if i want to keep ubuntu.) below is a sample of the svn script :  

 
 ```
 
  adding: wrf/multi/t2-skirmish2.wrf (stored 0%)
  adding: wrf/multi/t3-skirmish8.wrf (stored 0%)
  adding: wrf/multi/skirmish2.wrf (stored 0%)
  adding: wrf/multi/t2-skirmish8.wrf (stored 0%)
  adding: wrf/multi/skirmish8.wrf (stored 0%)
  adding: wrf/multi/t3-skirmish2.wrf (stored 0%)
  adding: wrf/multi/t2-skirmish4.wrf (stored 0%)
  adding: wrf/multi/skirmish4.wrf (stored 0%)
zip -T mp.wz
test of mp.wz OK
rm -f stamp
make[3]: Leaving directory `/home/ashki/warzone/data'
make[2]: Leaving directory `/home/ashki/warzone/data'
Making all in po
make[2]: Entering directory `/home/ashki/warzone/po'
make warzone2100.pot-update
make[3]: Entering directory `/home/ashki/warzone/po'
sed -e '/^#/d' remove-potcdate.sin > t-remove-potcdate.sed
mv t-remove-potcdate.sed remove-potcdate.sed
if LC_ALL=C grep 'GNU warzone2100' ../* 2>/dev/null | grep -v 'libtool:' >/dev/null; then \
      package_gnu='GNU '; \
    else \
      package_gnu=''; \
    fi; \
    if test -n 'warzone-dev@gna.org' || test 'http://wz2100.net/' = '@'PACKAGE_BUGREPORT'@'; then \
      msgid_bugs_address='warzone-dev@gna.org'; \
    else \
      msgid_bugs_address='http://wz2100.net/'; \
    fi; \
    case `: --version | sed 1q | sed -e 's,^[^0-9]*,,'` in \
      '' | 0.[0-9] | 0.[0-9].* | 0.1[0-5] | 0.1[0-5].* | 0.16 | 0.16.[0-1]*) \
        : --default-domain=warzone2100 --directory=.. \
          --add-comments=TRANSLATORS: --from-code=UTF-8 --no-wrap --width=1 --keyword=_ --keyword=N_ --keyword=P_:1c,2 --keyword=NP_:1c,2  \
          --files-from=./POTFILES.in \
          --copyright-holder='Warzone Resurrection Project' \
          --msgid-bugs-address="$msgid_bugs_address" \
        ;; \
      *) \
        : --default-domain=warzone2100 --directory=.. \
          --add-comments=TRANSLATORS: --from-code=UTF-8 --no-wrap --width=1 --keyword=_ --keyword=N_ --keyword=P_:1c,2 --keyword=NP_:1c,2  \
          --files-from=./POTFILES.in \
          --copyright-holder='Warzone Resurrection Project' \
          --package-name="${package_gnu}warzone2100" \
          --package-version='TRUNK' \
          --msgid-bugs-address="$msgid_bugs_address" \
        ;; \
    esac
test ! -f warzone2100.po || { \
      if test -f ./warzone2100.pot; then \
        sed -f remove-potcdate.sed < ./warzone2100.pot > warzone2100.1po && \
        sed -f remove-potcdate.sed < warzone2100.po > warzone2100.2po && \
        if cmp warzone2100.1po warzone2100.2po >/dev/null 2>&1; then \
          rm -f warzone2100.1po warzone2100.2po warzone2100.po; \
        else \
          rm -f warzone2100.1po warzone2100.2po ./warzone2100.pot && \
          mv warzone2100.po ./warzone2100.pot; \
        fi; \
      else \
        mv warzone2100.po ./warzone2100.pot; \
      fi; \
    }
make[3]: Leaving directory `/home/ashki/warzone/po'
test ! -f ./warzone2100.pot || \
      test -z "nb.gmo de.gmo da.gmo nl.gmo la.gmo it.gmo ru.gmo fr.gmo pt_BR.gmo es.gmo cs.gmo pl.gmo lt.gmo fy.gmo en_GB.gmo fi.gmo ga.gmo pt.gmo ro.gmo sl.gmo zh_CN.gmo zh_TW.gmo et_EE.gmo uk_UA.gmo hr.gmo" || make nb.gmo de.gmo da.gmo nl.gmo la.gmo it.gmo ru.gmo fr.gmo pt_BR.gmo es.gmo cs.gmo pl.gmo lt.gmo fy.gmo en_GB.gmo fi.gmo ga.gmo pt.gmo ro.gmo sl.gmo zh_CN.gmo zh_TW.gmo et_EE.gmo uk_UA.gmo hr.gmo
make[2]: Leaving directory `/home/ashki/warzone/po'
Making all in doc
make[2]: Entering directory `/home/ashki/warzone/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/ashki/warzone/doc'
Making all in icons
make[2]: Entering directory `/home/ashki/warzone/icons'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/ashki/warzone/icons'
Making all in pkg
make[2]: Entering directory `/home/ashki/warzone/pkg'
Making all in nsis
make[3]: Entering directory `/home/ashki/warzone/pkg/nsis'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/ashki/warzone/pkg/nsis'
make[3]: Entering directory `/home/ashki/warzone/pkg'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/ashki/warzone/pkg'
make[2]: Leaving directory `/home/ashki/warzone/pkg'
Making all in tests
make[2]: Entering directory `/home/ashki/warzone/tests'
(cd /home/ashki/warzone/data ; find base mods -name game.map > /home/ashki/warzone/tests/maplist.txt )
touch maplist.txt
make  all-am
make[3]: Entering directory `/home/ashki/warzone/tests'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/ashki/warzone/tests'
make[2]: Leaving directory `/home/ashki/warzone/tests'
make[2]: Entering directory `/home/ashki/warzone'
make[2]: Leaving directory `/home/ashki/warzone'
make[1]: Leaving directory `/home/ashki/warzone'
DONE!
run the following command for a system-wide install:
sudo make install
ashki@ashki-laptop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
ashki@ashki-laptop:~$ 

```So judging by this, how do i do a system wide install?... its should be simple but i have no clue yet.:confused:

---

