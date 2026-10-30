# demo-android

An Android library (`:relay`) that relays JSON events to partners' webhooks, in Kotlin on OkHttp 3.14.9, built with the Android Gradle Plugin 9.5 (its built-in Kotlin), a version catalog and the Gradle wrapper.

OkHttp is now at 5.x. For Kotlin callers its old functions are errors:
- `HttpUrl.parse(s)` → `s.toHttpUrlOrNull()`, `MediaType.parse(s)` → `s.toMediaTypeOrNull()` (moved to extension functions);
- `response.code()`, `request.url()`, `request.body()` → `response.code`, `request.url`, `request.body` (moved to vals);
- `RequestBody.create(type, s)` and `ResponseBody.create(type, s)` → `s.toRequestBody(type)` and `s.toResponseBody(type)`.

The unit tests answer calls with an interceptor, so they run offline: the resolved URL, method and content type, 2xx vs 500, and a bad base URL.

Teire demo repository: Teire should find the upgrade, read the Kotlin deprecation levels from the new jar, find the affected lines, move the catalog version, adapt the code, prove it with these tests before and after in its Android sandbox (SDK platforms 35 and 36), and open a verified pull request.

```bash
./gradlew build
```
