# schemav2validator Bug Fixes - Progress Tracker

Overall progress: **0/4 issues fixed**

---

## Issue 2: Domain whitelist bypass via substring match

**Status**: ✅ Completed  
**File**: `pkg/plugin/implementation/schemav2validator/extended_schema.go`  
**Function**: `isAllowedDomain()`

### Tasks
- [x] Add comprehensive test `TestIsAllowedDomain_Security()` in `extended_schema_test.go`
- [x] Verify test fails with current implementation
- [x] Implement fixed `isAllowedDomain()` function with proper URL parsing
- [x] Verify new test passes
- [x] Run full test suite to ensure no regressions
- [ ] Commit with message: "fix: secure domain whitelist check to prevent substring bypass"

---

## Issue 4: No timeout for initial OpenAPI spec URL load

**Status**: ⬜ Not started  
**File**: `pkg/plugin/implementation/schemav2validator/schemav2validator.go`

### Tasks
- [ ] Add `LoadTimeout int` field to `Config` struct (default 30)
- [ ] Add test `TestLoadSpec_URLTimeout()` in `schemav2validator_test.go`
- [ ] Verify test fails or hangs with current implementation (demonstrates no timeout)
- [ ] Modify `loadSpec()` to set `loader.Context` with timeout for URL loads
- [ ] Verify test passes (times out quickly)
- [ ] Run full test suite to ensure no regressions
- [ ] Commit with message: "feat: add configurable timeout for spec URL loading"

---

## Issue 6: isValidSchemaPath erroneously accepts empty paths

**Status**: ⬜ Not started  
**File**: `pkg/plugin/implementation/schemav2validator/extended_schema.go`  
**Function**: `isValidSchemaPath()`

### Tasks
- [ ] Add test case for empty string to `TestIsValidSchemaPath` in `extended_schema_test.go`
- [ ] Verify test fails (empty path currently returns true)
- [ ] Modify `isValidSchemaPath()` to explicitly reject empty/whitespace strings
- [ ] Verify test passes
- [ ] Run full test suite to ensure no regressions
- [ ] Commit with message: "fix: reject empty schema paths in isValidSchemaPath"

---

## Issue 8: Action extraction may miss deeply nested allOf

**Status**: ⬜ Not started  
**File**: `pkg/plugin/implementation/schemav2validator/schemav2validator.go`  
**Functions**: `extractActionFromSchema()`

### Tasks
- [ ] Create test spec with deeply nested `allOf` containing context/action
- [ ] Add test `TestValidate_DeepAllOfActionExtraction()` in `schemav2validator_test.go`
- [ ] Verify test fails with current implementation (action not found)
- [ ] Modify `extractActionFromSchema()` to recursively search all `allOf` branches
- [ ] Verify test passes
- [ ] Run full test suite to ensure no regressions
- [ ] Commit with message: "fix: support deeply nested allOf in action extraction"

---

## Final Steps (after all issues)

- [ ] Run comprehensive test suite: `go test ./pkg/plugin/implementation/schemav2validator/ -v`
- [ ] Run linting and formatting: `gofmt -w .` and `go mod tidy`
- [ ] Update README.md if documentation changes are needed (Issue 4 adds new config)
- [ ] Review all changes with `git diff` to ensure clean separation
- [ ] Push branch and create PR

---

## Notes

- Each issue must be a separate commit (4 commits total)
- Tests should fail before fix, pass after
- No breaking changes to existing behavior
- Maintain backward compatibility
