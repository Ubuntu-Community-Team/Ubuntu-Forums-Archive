---
title: "errors of compiling qtiplot 0.9.8.9"
date: 2011-11-23
forum: Education &amp; Science
---

### Post by chunri on 2011-11-23
I downloaded the latest source code of qtiplot from it's website, and then compiled it. Unfortunately, the compilation brought me a lot of errors which confused me. Can anyone help me? The following are output of terminal.

```
../tmp/qtiplot/main.o: In function `main':
main.cpp:(.text.startup+0x0): multiple definition of `main'
../tmp/qtiplot/minigzip.o:minigzip.c:(.text.startup+0x0): first defined here
../tmp/qtiplot/Integration.o: In function `evalFunction(double, void*)':
Integration.cpp:(.text+0x1d6): undefined reference to `mu::ParserBase::Eval() const'
../tmp/qtiplot/NonLinearFit.o: In function `NonLinearFit::setFormula(QString const&, bool)':
NonLinearFit.cpp:(.text+0x2676): undefined reference to `mu::ParserBase::Eval() const'
../tmp/qtiplot/FitDialog.o: In function `FitDialog::accept()':
FitDialog.cpp:(.text+0x131d1): undefined reference to `mu::ParserBase::Eval() const'
../tmp/qtiplot/IntDialog.o: In function `IntDialog::validInput(QString const&)':
IntDialog.cpp:(.text+0x1325): undefined reference to `mu::ParserBase::Eval() const'
IntDialog.cpp:(.text+0x1338): undefined reference to `mu::ParserBase::Eval() const'
../tmp/qtiplot/IntDialog.o:IntDialog.cpp:(.text+0x137f): more undefined references to `mu::ParserBase::Eval() const' follow
../tmp/qtiplot/MyParser.o: In function `MyParser::setLocale(QLocale const&)':
MyParser.cpp:(.text+0xb5): undefined reference to `mu::ParserBase::SetDecSep(char)'
MyParser.cpp:(.text+0xeb): undefined reference to `mu::ParserBase::SetThousandsSep(char)'
MyParser.cpp:(.text+0x104): undefined reference to `mu::ParserBase::ResetLocale()'
../tmp/qtiplot/MyParser.o: In function `MyParser::EvalRemoveSingularity(double*, bool) const':
MyParser.cpp:(.text+0x85d): undefined reference to `mu::ParserBase::Eval() const'
MyParser.cpp:(.text+0x8d6): undefined reference to `mu::ParserBase::Eval() const'
MyParser.cpp:(.text+0x955): undefined reference to `mu::ParserBase::Eval() const'
MyParser.cpp:(.text+0x9c3): undefined reference to `mu::ParserBase::Eval() const'
../tmp/qtiplot/muParserScript.o: In function `muParserScript::evalSingleLineToString(QLocale const&, char, int)':
muParserScript.cpp:(.text+0x1ea9): undefined reference to `mu::ParserBase::Eval() const'
../tmp/qtiplot/muParserScript.o:muParserScript.cpp:(.text+0x1f5e): more undefined references to `mu::ParserBase::Eval() const' follow
`.text._ZN11FrameWidgetD2Ev' referenced in section `.text._ZN11FrameWidgetD1Ev[FrameWidget::~FrameWidget()]' of ../tmp/qtiplot/sipqtiImageWidget.o: defined in discarded section `.text._ZN11FrameWidgetD2Ev[_ZN11FrameWidgetD5Ev]' of ../tmp/qtiplot/sipqtiImageWidget.o
../tmp/qtiplot/sipqtiAnova.o: In function `meth_Anova_run':
sipqtiAnova.cpp:(.text+0xfac): undefined reference to `Anova::run()'
../tmp/qtiplot/sipqtiAnova.o: In function `sipAnova::logInfo()':
sipqtiAnova.cpp:(.text+0x1070): undefined reference to `Anova::logInfo()'
../tmp/qtiplot/sipqtiAnova.o: In function `meth_Anova_logInfo':
sipqtiAnova.cpp:(.text+0x1160): undefined reference to `Anova::logInfo()'
../tmp/qtiplot/sipqtiAnova.o: In function `meth_Anova_addSample':
sipqtiAnova.cpp:(.text+0x126f): undefined reference to `Anova::addSample(QString const&, int, int)'
../tmp/qtiplot/sipqtiAnova.o: In function `sipAnova::qt_metacall(QMetaObject::Call, int, void**)':
sipqtiAnova.cpp:(.text+0x187f): undefined reference to `Anova::qt_metacall(QMetaObject::Call, int, void**)'
../tmp/qtiplot/sipqtiAnova.o: In function `sipAnova::run()':
sipqtiAnova.cpp:(.text+0x1924): undefined reference to `Anova::run()'
../tmp/qtiplot/sipqtiAnova.o: In function `sipAnova::sipAnova(ApplicationWindow*, bool, double)':
sipqtiAnova.cpp:(.text+0x1b65): undefined reference to `Anova::Anova(ApplicationWindow*, bool, double)'
../tmp/qtiplot/sipqtiAnova.o: In function `sipAnova::~sipAnova()':
sipqtiAnova.cpp:(.text+0x233b): undefined reference to `vtable for Anova'
sipqtiAnova.cpp:(.text+0x237e): undefined reference to `vtable for Anova'
../tmp/qtiplot/sipqtiAnova.o: In function `sipAnova::qt_metacast(char const*)':
sipqtiAnova.cpp:(.text+0x1b1f): undefined reference to `Anova::qt_metacast(char const*)'
../tmp/qtiplot/sipqtiAnova.o:(.data+0xb4): undefined reference to `Anova::staticMetaObject'
../tmp/qtiplot/sipqtiAnova.o:(.rodata._ZTI8sipAnova[typeinfo for sipAnova]+0x8): undefined reference to `typeinfo for Anova'
../tmp/qtiplot/sipqtiAnova.o:(.rodata._ZTV8sipAnova[vtable for sipAnova]+0x40): undefined reference to `Anova::freeMemory()'
../tmp/qtiplot/sipqtiAnova.o:(.rodata._ZTV8sipAnova[vtable for sipAnova]+0x58): undefined reference to `Anova::resultTable(QString const&)'
../tmp/qtiplot/sipqtiAnova.o:(.rodata._ZTV8sipAnova[vtable for sipAnova]+0x5c): undefined reference to `Anova::outputResultsTo(Table*)'
`.text._ZN11ImageWidgetD2Ev' referenced in section `.text._ZN11ImageWidgetD1Ev[non-virtual thunk to ImageWidget::~ImageWidget()]' of ../tmp/qtiplot/moc_ImageWidget.o: defined in discarded section `.text._ZN11ImageWidgetD2Ev[_ZN11ImageWidgetD5Ev]' of ../tmp/qtiplot/moc_ImageWidget.o
collect2: ld returned 1 exit status
make[1]: *** [qtiplot] Error 1
make[1]: Leaving directory `/home/flying/Downloads/qtiplot-0.9.8.9/qtiplot'
make: *** [sub-qtiplot-make_default] Error 2

```

---

### Post by volfoni54 on 2011-12-03
Hello,

I think you attempted several compilations. If so, try to do a 'make clean' and then to recompile (make).

Good luck, QtiPlot is not easy to compile.

Raoul

---

### Post by jat255 on 2012-06-29
Hello chunri,

Did you ever have any success in compiling qtiplot 0.9.8.9?  I'm working on doing so right now and was hoping you might have a few tips!

Thanks,
Josh

---

### Post by jat255 on 2012-08-07
Hello chunri,

I'm not sure if you ever got this working, but I managed to, and I outlined how I was able to do it [here]("http://www.terpconnect.umd.edu/~jtaillon/qtiplot.php").

Hopefully that's of some help to you or anyone else that comes looking for answers.

- Josh

---

