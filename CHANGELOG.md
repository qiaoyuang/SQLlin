# SQLlin Change Log

- Date format: YYYY-MM-dd

## 1.4.4 / 2025-07-07

### All

* Update `Kotlin`'s version to `2.2.0`

### sqllin-dsl

* Update `kotlinx.serialization`'s version to `1.9.0`

### sqllin-driver

* Update the `sqlite-jdbc`'s version to `3.50.2.0`

### sqllin-processor

* Update `KSP`'s version to `2.2.0-2.0.2`

## v1.4.3 / 2025-06-02

### All

* Update `Kotlin`'s version to `2.1.21`

### sqllin-processor

* Update `KSP`'s version to `2.1.21-2.0.1`

## v1.4.2 / 2025-04-23

### All

* Update `Kotlin`'s version to `2.1.20`

### sqllin-dsl

* Update `kotlinx.coroutines`'s version to `1.10.2`
* Update `kotlinx.serialization`'s version to `1.8.1`

### sqllin-driver

* Update the `sqlite-jdbc`'s version to `3.49.1.0`

### sqllin-processor

* Update `KSP`'s version to `2.1.20-1.0.32`

## v1.4.1 / 2025-02-04

### All

* Update `Kotlin`'s version to `2.1.10`

### sqllin-dsl

* Update `kotlinx.coroutines`'s version to `1.10.1`
* Update `kotlinx.serialization`'s version to `1.8.0`
* Add some DslMaker annotations, make the DSL apis be more readable

### sqllin-driver

* Update the `sqlite-jdbc`'s version to `3.48.0.0`

### sqllin-processor

* Update `KSP`'s version to `2.1.10-1.0.29`

## v1.4.0 / 2024-12-04

### All

* Update `Kotlin`'s version to `2.1.0`

### sqllin-dsl

* Update `kotlinx.coroutines`'s version to `1.9.0`
* Update `kotlinx.serialization`'s version to `1.7.3`

### sqllin-driver

* Update the `sqlite-jdbc`'s version to `3.47.1.0`

### sqllin-processor

* Update `KSP`'s version to `2.1.0-1.0.29`

## v1.3.2 / 2024-06-18

### All

* Update `Kotlin`'s version to `1.9.24`

### sqllin-dsl

* Now, you can annotate properties with `kotlinx.serialization.transmint` in your data classes to ignore these properties when serialization or deserialization and `Table` classes generation.

### sqllin-processor

* Update `KSP`'s version to `1.9.24-1.0.20`

## v1.3.1 / 2024-04-24

### sqllin-dsl

* Fix a crash when a data class doesn't contain any `String` element.
* Fix the [issue#81](https://github.com/ctripcorp/SQLlin/issues/81) about insert and query null values
* Fix some wrongs about generation of SQL syntax

### sqllin-driver

* **Breaking change**: Remove the deprecated API `CommonCursor#forEachRows`
* **Breaking change**: the `getInt`, `getLong`, `getFloat` and `getDouble` will throw an exception when the value is NULL in SQLite
* Add a new public API: `CommonCursor#isNull`, for check if the value is NULL in SQLite

## v1.3.0 / 2024-04-21

### All

* Update `Kotlin`'s version to `1.9.23`

### sqllin-dsl

* Update `kotlinx.coroutines`'s version to `1.8.0`
* Update `kotlinx.serialization`'s version to `1.6.3`
* Modify the SQL statements' splicing method, that fixed the [issue#77](https://github.com/ctripcorp/SQLlin/issues/77) that users can't read/write special symbols as the values in SQL statements.
* Performance optimization, use `ArrayDeque` to replace the LinkedList for SQL statements management (self-implemented).
* The parameter `enableSimpleSQLLog` of the `Database`'s constructors of is `false` by default.

### sqllin-driver

* Update the `sqlite-jdbc`'s version to `3.45.3.0`

### sqllin-processor

* Update `KSP`'s version to `1.9.23-1.0.20`

## v1.2.4 / 2024-01-05

### All

* Update `Kotlin`'s version to `1.9.22`

### sqllin-dsl

* Update `kotlinx.serialization`'s version to `1.6.2`

### sqllin-processor

* Update `KSP`'s version to `1.9.22-1.0.16`

## v1.2.3 / 2023-11-28

### All

* Update `Kotlin`'s version to `1.9.21`

### sqllin-dsl

* Now, the `ORDER_BY` clause could ignore the `OrderByWay` parameter like SQL.
* Optimize the performance in concurrent scenarios. Some types have changed, but users don't need to change the code.
* Now, `SelectStatement` has been changed to lazy deserialization mode, that's means the first time you invoke the 
function `SelectStatement#getResults` will consume more time. But, correspondingly, executing `SELECT` statements will be faster.
* Add the `enableSimpleSQLLog` parameter to `Database`'s constructor, default by `true`, if you set it to
`false`, you can disable the simple SQL logout.

### sqllin-driver

* Deprecated the public API `CommonCursor#forEachRows`, you can replace with `CommonCursor#forEachRow`. This
change just for fixing a typo :). And, the `CommonCursor#forEachRows` will be removed in next version.

### sqllin-processor

* Update `KSP`'s version to `1.9.21-1.0.15`

## v1.2.2 / 2023-11-08

### All

* Update `Kotlin`'s version to `1.9.20`

### sqllin-dsl

* Add the new native target support: `linuxArm64`
* Add the new API `Database#suspendedScope`, it could be used to ensure concurrency safety([#55](https://github.com/ctripcorp/SQLlin/pull/55))
* Begin with this version, _sqllin-dsl_ depends on _kotlinx.coroutines_ version `1.7.3`
* **Breaking change**: Remove the public class `DBEntity`, we have deprecated it in version `1.1.1`

### sqllin-driver

* Add the new native target support: `linuxArm64`

### sqllin-processor

* Update `KSP`'s version to `1.9.20-1.0.13`
* Fix the bug for when the code that is generated by `sqllin-processor` can't be compiled([#58](https://github.com/ctripcorp/SQLlin/pull/58))

## v1.2.1 / 2023-10-18

### All

* Update `Kotlin`'s version to `1.9.10`

### sqllin-driver

* Fix the problem: [Native driver does not respect isReadOnly](https://github.com/ctripcorp/SQLlin/issues/50). ***On native platforms***. 
Now, if a user set `isReadOnly = true` in `DatabaseConfigurtaion`, the database file must exist. And, if opening in read-write mode 
fails due to OS-level permissions, the user will get a read-only database, and if the user try to modify the database, will receive
a runtime exception. Thanks for [@nbransby](https://github.com/nbransby).

### sqllin-processor

* Update `KSP`'s version to `1.9.10-1.0.13`
* Now, if your data class with `@DBRow` can't be solved or imported successfully(Using `KSNode#validate` to judge), the
`ClauseProcessor` would try to resolve it in second round.

## v1.2.0 / 2023-09-19

### sqllin-dsl

* Add the new JVM target

### sqllin-driver

* Add the new JVM target
* **Breaking change**: Remove the public property: `DatabaseConnection#closed`
* The Android (< 9) target supports to set the `journalMode` and `synchronousMode` now

## v1.1.1 / 2023-08-12

### All

* Update `Kotlin`'s version to `1.9.0`

### sqllin-dsl

* Deprecated the public API `DBEntity`([#36](https://github.com/ctripcorp/SQLlin/pull/36), [#37](https://github.com/ctripcorp/SQLlin/pull/37)), any data classes used in _sqllin-dsl_ don't need to extend `DBEntity` anymore.

### sqllin-driver

* Fix a bug about empty `ByteArray` on native platforms([#30](https://github.com/ctripcorp/SQLlin/pull/30))

### sqllin-processor

* Update `KSP`'s version to `1.9.0-1.0.13`

## v1.1.0 / 2023-06-06

### All

* Remove the `iosArm32`, `watchosX86` and `mingwX86` these three targets' support
* Add the new native target support: `watchosDeviceArm64`

### sqllin-dsl

* Update `kotlinx.serialization`'s version to `1.5.1`

### sqllin-driver

* Enable the `New Native Driver` to replace [SQLiter](https://github.com/touchlab/SQLiter)
* Make some unnecessary APIs be internal (`CursorImpl`, `DatabaseConnectionImpl` and more...)
* Add the new public function in `Cursor#next`
* Add the new public function `deleteDatabase`
* Add the new public property: `DatabaseConnection#isClosed`
* Deprecated the public property: `DatabaseConnection#closed`

## v1.0.1 / 2023-05-14

### All

* Update `Kotlin`'s version to `1.8.20`

### sqllin-dsl

* Update `kotlinx.serialization`'s version to `1.5.0`

### sqllin-processor

* Update `KSP`'s version to `1.8.20-1.0.11`

## v1.0.0 / 2022-12-29

### All

* Fix some bugs about unit tests

### sqllin-dsl

* Add the `ON` clause support
* Fix some bugs about `JOIN` clause

### sqllin-processor

* Update `KSP`'s version to `1.7.20-1.0.8`

## v1.0-alpha01 / 2022-11-29

### Initial Release

* Based on `Kotlin 1.7.20`
* Based on `KSP 1.7.20-1.0.7`
* Based on `kotlinx.serialization 1.4.1`