# notes-codemotion-warsaw-2016

## 1. "Navigating all the knowledge" James Weaver

Prelekcja typu Keynote. Ten typ prelekcja jest szczególny podczas
konferencji, ze względu na to, że zawsze takie prelekcje prowadzą
dosyć znane osobistości i poruszają interesujące tematy.

James jest kimś pokroju Java Ninja.
Napisał kilka książek. Stworzył kilka dużych projektów.
O jednym z nich opowiedział.

James opowiedział o projekcie ConceptMap (http://conceptmap.cfapps.io/)
Pokazywał jak działa aplikacja na przykładzie pokazania zależności
między Robertem Lewandowski a Michałem Pazdanem.

## 2. "Make your own USB device for free!" Krzysztof Opasiak

* https://github.com/kopasiak

Krzysiek opowiedział zasadę działania USB.
Mogliśmy się dowiedzieć jak działa Plug and Play,
czyli podłączenie urządzenia do np. komputera,
tym samym po kilku sekundach automatycznej konfiguracji
urządzenie powinno być gotowe do używania.

Limit urządzeń podłączonych to 31 sztuk.
Dziwnie blisko 2 ^^ 6 - jest to ograniczenie hardware-owe.

Prelegent opowiedział o sterownikach do protokołu USB.
USB device  = UDC + USB gadget
UDC drive - for USB device controller
Phonet - Nokia 100 protocol

Projekt prelegenta do lekkiej automatyzacji USB gadgetów:
https://github.com/kopasiak/gt

Testowa aplikacja prelegenta:
https://github.com/kopasiak/simple_usb_chat

## 3. "Let’s demystify IoT for Java developers (with a drone!)" Ville Ingman

Trzecia prezentacja była mega dynamiczna - mieliśmy w sali drona!
Poprawna nazwa to Quadrocopter.

Mogliśmy skorzystać z http://vaadindrone-social.mybluemix.net/
aby zaświecić światełka w tejże maszynie latającej.

Prelegent opowiadał o module Vaadin.

## 4. "Geospatial Graphs made easy with OrientDB" Luigi Dell Aquila

* http://twiter.com/idellaquila

Prelegent opowiadał o bazie danych OrientDB pisząc kawałek kodu,
który czyta pliki w formacie CSV i wrzuca do klasy (takie jest określenie
tabeli w OrientDB)

Drugą część prezentacji Luigi oparł o swój projekt:
https://github.com/luigidellaquila/geospatial-demo

## 5. "Getting started with Go" Florin Patan

Florian opowiadał o początkach Go.

Więcej info tutaj: http://warsaw2016.codemotionworld.com/wp-content/themes/event/detail-talk.php?detail=4012

## 6. "RxJS - destroy the state machine!" Stenver Jerkku

Więcej info tutaj: http://warsaw2016.codemotionworld.com/wp-content/themes/event/detail-talk.php?detail=3848

## 7. "Extending JS" Francis Bourre

"Transpiling JS is mainstream"

W firmie prelegenta nie lubi się Singletonów.

Więcej: http://warsaw2016.codemotionworld.com/wp-content/themes/event/detail-talk.php?detail=4518

---
---
---

## 1. "Angular2 and Redux - up & running" Nir Kaufman

Principle

1: Redux to wzorzec projektowy, a nie biblioteka.
2: Stan jest tylko do odczytu.
3: pure functions (reducer)
Tworzymy po za stanem.
Następny state jest zawsze immutable

Store jest sercem Reduxa
Aby stworzyć store musimy mieć co najmniej 1 reducera.

Predictable state container
Dla tych samych danych wejściowych mamy ten sam stan.

### Store API

* `dispatch(action)`
* `subscribe(listener)`
* `getState()`
* `replaceReducer(reducer)`

Więcej: http://warsaw2016.codemotionworld.com/wp-content/themes/event/detail-talk.php?detail=3665

## 2. "Reverse engineering the clean code" Jakub Marchwicki

* http://twitter.com/kubem
* jakub.marchwicki.pl

"Jeśli jesteś programistą Java na pewno widziałeś dużo złego kodu"

Books
 - "czysty kod" niebieska okładka
 - "wzorce implementacyjne" kent beck

Liczba 7 jest bardzo popularna.

Więcej: http://warsaw2016.codemotionworld.com/wp-content/themes/event/detail-talk.php?detail=4522

## 3. "Get started writing TypeScript today!" Dominik Kundel

* http://twitter.com/dkundel

"typescript" & "typings" - potrzebne aby uruchomić plik TSa
Nie trzeba instalować globalnie, wystarczy lokalnie.

TData

### require w kodzie?

* hacky way

    ```
    declare const require: Function;
    ```

* typings definition files
    - nie mają żadnej logiki
    - zawierają definicję typów
    
    ```
    typigns install env~node --global --save
    ```

---

* a potem dodać:
    ```
    tsc db.ts typings/index.d.ts
    ```

* tsconfig.json
    ```json
    {
        "compilerOptions": {
            "module": "commonjs",
            "outDir": "output",
            "allowJs": true,
            "target": "es2015"
    
            "noImplicitAny": true,
            "noImplicitThis": true,
            "sourceMap": true,
            "inlineSourceMap": true # top of JS file
        }
    }
    ```
* a potem
    ```
    import event = require('events');
    ```
* a potem w konkretnej klasie
    ```
    class Test extends events.EventEmitter
    ```
* a potem w constructor() dodać
    ```
    super();
    ```
* na końcu
    ```
    node_modules/.bin/tsc # bez parametrów
    ```

Nie musisz używać TS do małego projektu.
Warto używać do dużego.

Lepsze doświadczenia z developowania.

http://bit.ly/startTypeScript - blog post autora

http://bit.ly/codemotion-typescript

Więcej: http://warsaw2016.codemotionworld.com/wp-content/themes/event/detail-talk.php?detail=4387

## 4. "Unlock the power of JavaScript Decorators" Nir Kaufman

Deko dodają zachowanie do klas, metod, właściwości nie zmienią innych części klasy.
Dekorator to proste funkcja, który daje dostęp do czegoś co musi być udekorowane.
Korzystamy ze znaku małpki - @ - jako prefix

Dekoratory klas korzystają z konstruktora klasy.

Ładnie wygląda kod z kontenerze z zaokrąglonymi rogami

Fabryka dekoratorów - przekazywanie parametrów do dekoratora
przyjmuje target, czyli definicję klasy
* @freeze
* @singleton

Property decorator - Przyjmuje ona 2 parametry: object, propertyKey
* @json
* @format

Method decorator - Przyjmuje 3 par: constructor, propertyKey, keyDescriptor
* @protect

Parameter decorator

Reflaction - Przyjmuje 3 parametry: prototype, methodName, parameterIndex
* @validate

Implementacja wzorca Dependency Injection

Więcej: http://warsaw2016.codemotionworld.com/wp-content/themes/event/detail-talk.php?detail=3664

## 5. "Breaking Bad with GitLab CI" Ivan Nemytchenko

* http://twitter.com/inek
* inem@bk.ru

Więcej: http://warsaw2016.codemotionworld.com/wp-content/themes/event/detail-talk.php?detail=3930

Ivan opowiadał jak krok po kroku zaimplementować w swojej firmie.

## 6. "Regex fundamentals" Juliette Reinders Folmer

* http://regexcheatsheet.com/

Więcej: http://warsaw2016.codemotionworld.com/wp-content/themes/event/detail-talk.php?detail=4055

"regex are wildcards on steroids"

W regexpach chodzi o wzorzec

### whitelisting vs blacklisting

Jak działają?

* tworzenie wzorca
* potem wyrażenia regularnego
* temat
* function
* no i mamy wynik!

jakie pytania?

* czy pasuje?
* ile dopasować?
* jakie dopasowania?

regex engines

* posix
* jakarta
* frej
* deelx
* pcre
* rgx
* emascript
* tre
* qt
* boost
* pattwo
* greta
* oniguruma
* RE2
* henry spences regex
* glib/gregex

terminologia

* regular expression
* delimiters
* modifiers

basic syntax

* literals: Aa1
* wildcard: .
* quantifiers: ?+*{#}
* character ranges [..]
* grouping and alternation: (...|...)
* anchors ^..,$
* shorthand characters code \w\d\s
* modifiers: gmsi

Zasięg działają zgodnie z tablicą ASCII, np. a-z - zadziała, ale z-a już nie

Testowaliśmy wyrażenie regularne do definicji koloru w formacie RGB pisany szesnastkowo np. #ab1234
http://regexper.com/

### Tips & tricks

(?:&lt;expr&gt;) - nie bierzemy pod uwagę wszystkich dopasowań

[^&lt;chars*gt;] - negatywna klasa

* backtracing - przeszukiwanie wzorca od końca poprzedniego dopasowania

* reluctant quantifiers

\b nie można łapać bo to nie jest znak

na początku wzorca zawsze podaje się dłuższe wzorce, bo inaczej te krótsze od razu znajdą krótszą frazę

déjà vu [\w ]+  -------- fail on english (en)
déjà vu [\w ]+  -------- success on french (fr)

[(] nie potrzebuje już eskejpowania, bo pisany normalnie potrzebuje \(

\\\\ matching literal backslash

regex + modifier = engine behaviour

* settings (?i)
* unsettings (?-i)
* combined (?im-sx)
* apply to subpattern non-capturing (?i:subp)

advanced feature

* look around
* name sb-matches
* recursion
* inline comments
* conditional sub-patters
