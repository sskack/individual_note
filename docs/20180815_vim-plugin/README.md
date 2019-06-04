# VIM Plugin
## Plugin-Manager
### vim-plug
- Install
```
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim 
```
    - Proxyが必要な場合
    ```
    export http_proxy=xxx
    export https_proxy=xxx
    ```
    - Proxyのクレデンシャルが必要かつ記号が入ってる場合
    ```
    export http_proxy=id:password@xxx:8080
    export https_proxy=id:password@xxx:8080
    # p@ssword なら p%40ssword で URLエンコーディングを指定する
    ```

- vim-plug 使い方
    - 上記curlでvimplug入手
    - vim 起動
    - `:PlugInstall`
* .vimrc
```
if has('vim_starting')
  set rtp+=~/.vim/plugged/vim-plug
  if !isdirectory(expand('~/.vim/plugged/vim-plug'))
    echo 'install vim-plug...'
    call system('mkdir -p ~/.vim/plugged/vim-plug')
    call system('git clone https://github.com/junegunn/vim-plug.git ~/.vim/plugged/vim-plug/autoload')
  end
endif

call plug#begin('~/.vim/plugged')
  Plug 'junegunn/vim-plug',
        \ {'dir': '~/.vim/plugged/vim-plug/autoload'}
  Plug 'itchyny/lightline.vim'
call plug#end()

```
* .vimrc
```
syntax on
set laststatus=2
set autoindent
"vi互換を切る
set nocompatible
"タブの代わりに空白文字を挿入する
set expandtab
"変更中のファイルでも、保存しないで他のファイルを表示
set hidden
"インクリメンタルサーチを行う
set incsearch
"シフト移動幅
set shiftwidth=4
"対応する括弧を表示する
set showmatch
"検索時に大文字を含んでいたら大/小を区別
set smartcase
"高度な自動インデントを行う
set smartindent
"行頭の余白内で Tab を打ち込むと、'shiftwidth' の数だけインデントする。
set smarttab
"検索をファイルの先頭へループしない
set nowrapscan
"256色配色を用いる
set t_Co=256
"カラースキーマを指定する（ここではmolokai）
if &term == "xterm-256color"
    colorscheme molokai
    hi Comment ctermfg=102
    hi Visual  ctermbg=236
endif
set noshowmode
let g:lightline = {
      \ 'colorscheme': 'powerline',
      \ }
```
- Molokai設定
    - Molokai普通に導入
    - Molokai
    ```
    # vimrcの以下記述でコメントアウトがいい感じに表示される
    hi Comment ctermfg=102
    hi Visual  ctermbg=236
    ```
    - Molokai の背景を黒にする    
    https://lowply.github.io/blog/2012/08/patch-to-disable-molokai-bgcolor/
- Tereterm の フォントを Rictyに変更
    - Ricty Diminished を入手して windowsにいれる
        - RictyDiminished-Regular.ttf
    - Tereterm のフォント設定を変更
        - 文字の大きさは 13がおすすめ
