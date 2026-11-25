# CampusBoot

A mini annotation-driven framework built with Java Reflection (Java 11+, no external libraries).

## Files

| File | Purpose |
|------|---------|
| `Component.java` | `@Component` - marks a class as a bean (class level) |
| `Value.java` | `@Value` - injects a config value into a field |
| `Range.java` | `@Range` - int field must be within `min`..`max` |
| `Route.java` | `@Route` - maps a URL path to a method |
| `Container.java` | `scan`, `injectValues`, `getBean` (IoC + value injection) |
| `Validator.java` | `validate(Object)` - checks `@Range` fields |
| `Router.java` | `dispatch(Container, String)` - invokes `@Route` methods |
| `GradeController.java`, `ReportPrinter.java`, `Student.java`, `Main.java` | Starter code |
| `answers.txt` | Part E reflection answers |

## Note

The starter code uses `@Route("/hello")`, so `Route` declares both `value()` and `path()`; `Router` matches either.

## Compile and Run

```
javac *.java
java Main
```

All `.java` files must be in the same folder.

## Expected Output

```
[Container] Registered: gradeController (GradeController)
[Container] Skipped: ReportPrinter (no @Component)
[Container] Injected: app.name -> GradeController.appName
[Container] Injected: app.passMark -> GradeController.passMark
--- Validation ---
VIOLATION: score - Score must be between 0 and 100 (actual: 120)
OK
VIOLATION: semester - Value out of range (actual: 15)
--- Routing ---
[Router] /hello -> Welcome to CampusBoot
[Router] /status -> Pass mark is 40
[Router] /unknown -> 404 Not Found: /unknown
```
