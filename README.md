# _InputZ deatils

a Sass (.scss) based css framework for input,form elements embressing the new web concepts. 

## Getting Started

* visit https://inputz.herokuapp.com/download to customize and download the required files. 
* use your prefered method for handing .scss and compressing .js files . we use gulp

### Prerequisities

copy and attach the downloaded files to your project

###Gulp workflow (optional)
```
var gulp = require('gulp'),
    
    //css related
    sass = require('gulp-sass'),
    sourcemaps = require('gulp-sourcemaps'),
    prefix = require('gulp-autoprefixer'),
    combineMq = require('gulp-combine-mq'),
    
    //js related
    uglify = require('gulp-uglify'),

// source and destination folder names
var source = <folder Name>,
    destination = <folder Name>;

// scssToCss
gulp.task('scssToCss', function () {
    gulp.src(source + '/scss/**/*.scss')
        .pipe(sourcemaps.init())
        .pipe(sass({
            outputStyle: 'expanded'
        }))
        .pipe(prefix('last 2 versions'))
        .pipe(combineMq({
            beautify: true
        }))
        .pipe(sourcemaps.write('../sourceMaps_css'))
        .pipe(gulp.dest(destination + '/css/'));
});

// js compress
gulp.task('jsComp', function() {
  return gulp.src(source + '/scripts/*.js')
    .pipe(uglify())
    .pipe(gulp.dest(destination + '/js'));
});

/* Watch for changes */
/* Generic */
gulp.task('watch', function () {
    gulp.watch(source + '/scss/**/*.scss', ['scssToCss']),
    gulp.watch(source + '/scripts/*.js', ['jsComp']);
});

/* Default Gulp task */
gulp.task('default', ['scssToCss','jsComp' , 'watch']);

```
